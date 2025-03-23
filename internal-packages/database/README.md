<div align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
  <source media="(prefers-color-scheme: light)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/3f5ad4c1-c4c8-4277-b622-290e7f37bd00/public">
  <img alt="Trigger.dev logo" src="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
</picture>
  
### Database Package for Trigger.dev

[Discord](https://trigger.dev/discord) | [Website](https://trigger.dev) | [Issues](https://github.com/triggerdotdev/trigger.dev/issues) | [Docs](https://trigger.dev/docs)

[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/triggerdotdev.svg?style=social&label=Follow%20%40trigger.dev)](https://twitter.com/triggerdotdev)

</div>

# @trigger.dev/database

This is the internal database package for the Trigger.dev platform. It exports a generated Prisma client that can be instantiated with a connection string.

## Package Purpose

The database package serves as the data layer for the Trigger.dev platform, providing:

- Database schema definitions via Prisma
- Type-safe database client
- Migration management
- Database utility functions
- Data access patterns for various components

## Key Features

- **Prisma Schema**: Complete data model for the platform
- **Migration Management**: Tools for managing database migrations
- **Typesafe Access**: Generated TypeScript types for database interactions
- **Utility Functions**: Common database operations and helpers
- **Connection Management**: Pooling and connection handling

## Schema Overview

The database schema includes models for:

- Users and authentication
- Projects and environments
- Tasks and triggers
- Runs and execution logs
- API keys and integrations
- Worker groups and workers
- Schedules and events

## Usage

This package is used internally by other Trigger.dev components:

```typescript
import { prisma } from "@trigger.dev/database";

// Example: Fetch tasks for a project
const tasks = await prisma.task.findMany({
  where: { projectId: "project-id" },
  include: { runs: true }
});
```

## Development Commands

```bash
# Generate Prisma client
pnpm run generate

# Create a new migration
pnpm run db:migrate:dev:create

# Deploy migrations
pnpm run db:migrate:deploy

# Push schema changes without migrations
pnpm run db:push

# Open Prisma Studio for database browsing
pnpm run db:studio

# Reset the database (caution!)
pnpm run db:reset
```

## How to switch branches when you've done migrations

Sometimes you've applied migrations and then want to switch branches without wiping out your local database.

To do this you can run the following command:

```bash
DB_VOLUME=database-data-alt pnpm run docker
```

This will switch to the `alt` volume for your local database. This database will be blank if you haven't switched to this volume before, so you'll need to follow the normal steps (in the Contributing guide) to get setup, e.g. apply migrations and seed.

To switch back to the original volume, run the following command:

```bash
pnpm run docker
```

## How to add a new index on a large table

1. Modify the Prisma.schema with a single index change (no other changes, just one index at a time)
2. Create a Prisma migration using `cd internal-packages/database && pnpm run db:migrate:dev --create-only`
3. Modify the SQL file: add IF NOT EXISTS to it and CONCURRENTLY:

```sql
CREATE INDEX CONCURRENTLY IF NOT EXISTS "JobRun_eventId_idx" ON "JobRun" ("eventId");
```

4. Don't apply the Prisma migration locally yet. This is a good opportunity to test the flow.
5. Manually apply the index to your database, by running the index command.
6. Then locally run `pnpm run db:migrate:deploy`

### Before deploying

Run the index creation before deploying

```sql
CREATE INDEX CONCURRENTLY IF NOT EXISTS "JobRun_eventId_idx" ON "JobRun" ("eventId");
```

These commands are useful:

```sql
-- creates an index safely, this can take a long time (2 mins maybe)
CREATE INDEX CONCURRENTLY IF NOT EXISTS "JobRun_eventId_idx" ON "JobRun" ("eventId");
-- checks the status of an index
SELECT * FROM pg_stat_progress_create_index WHERE relid = '"JobRun"'::regclass;
-- checks if the index is there
SELECT * FROM pg_indexes WHERE tablename = 'JobRun' AND indexname = 'JobRun_eventId_idx';
```

Now, when you deploy and prisma runs the migration, it will skip the index creation because it already exists. If you don't do this, there will be pain.

## Dependencies

- Prisma ORM and client
- PostgreSQL database (primary)

## For Developers

When making schema changes:

1. Modify the Prisma schema in `prisma/schema.prisma`
2. Create a migration: `pnpm run db:migrate:dev:create`
3. Apply the migration: `pnpm run db:migrate:deploy`
4. Regenerate the client: `pnpm run generate`
5. Update any affected code in other packages

This package is critical infrastructure for the platform, so schema changes should be carefully considered and tested.
