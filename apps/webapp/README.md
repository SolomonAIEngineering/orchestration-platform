<div align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
  <source media="(prefers-color-scheme: light)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/3f5ad4c1-c4c8-4277-b622-290e7f37bd00/public">
  <img alt="Trigger.dev logo" src="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
</picture>
  
### Trigger.dev Web Application

[Discord](https://trigger.dev/discord) | [Website](https://trigger.dev) | [Issues](https://github.com/triggerdotdev/trigger.dev/issues) | [Docs](https://trigger.dev/docs)

[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/triggerdotdev.svg?style=social&label=Follow%20%40trigger.dev)](https://twitter.com/triggerdotdev)

</div>

# Trigger.dev Web Application

The Trigger.dev webapp is the main user interface for the platform, providing a dashboard for managing, monitoring, and debugging background tasks. This application is built using Remix, a full-stack web framework.

## Package Purpose

The webapp serves as the primary interface for:

- User account management
- Project creation and configuration
- Task monitoring and debugging
- Environment management
- API key administration
- Log viewing and analysis
- Integration configuration
- Real-time task execution monitoring
- Analytics and insights

## Key Features

- **Interactive Dashboard**: Monitor and manage all your tasks
- **Task Explorer**: Browse, search, and filter tasks
- **Run History**: View detailed history of all task executions
- **Real-time Logs**: Stream logs from running tasks
- **Trace Viewer**: Visualize task execution paths
- **Integration Management**: Configure and connect external services
- **Environment Controls**: Manage development, staging, and production environments
- **Team Collaboration**: Share projects and tasks with team members
- **API Key Management**: Create and revoke API keys

## Technology Stack

- **Frontend**: React, TailwindCSS, Framer Motion
- **Framework**: Remix (React Router-based full-stack framework)
- **Database**: Prisma ORM with PostgreSQL
- **Real-time**: Socket.io
- **Authentication**: Custom auth system with GitHub OAuth integration
- **Monitoring**: OpenTelemetry

## Development

To start the development server:

```sh
pnpm run dev --filter webapp
```

This will start the application on port 3030 by default.

## Building and Deployment

### Local Build

```sh
pnpm run build --filter webapp
```

### Docker Build

```sh
pnpm run docker:build:webapp
docker run -it -p 3030:3030 triggerdotdev-webapp
```

## Environment Configuration

The application requires several environment variables to run properly. See `.env.example` at the root of the monorepo for all available options.

Key environment variables include:
- `DATABASE_URL`: PostgreSQL connection string
- `REDIS_URL`: Redis connection string
- `SESSION_SECRET`: Secret for session encryption
- `GITHUB_CLIENT_ID` and `GITHUB_CLIENT_SECRET`: For GitHub authentication

## Testing

```sh
pnpm run test --filter webapp
```

## Design System

The webapp uses a custom design system built on TailwindCSS, with accessibility as a core principle. Components are designed to be responsive and follow best practices for web applications.

## For Developers

If you're contributing to Trigger.dev, this application is the main interface that users interact with. It communicates with various backend services to provide a unified experience for managing background tasks.
