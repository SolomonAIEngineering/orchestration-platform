<div align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
  <source media="(prefers-color-scheme: light)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/3f5ad4c1-c4c8-4277-b622-290e7f37bd00/public">
  <img alt="Trigger.dev logo" src="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
</picture>
  
### Trigger.dev Supervisor

[Discord](https://trigger.dev/discord) | [Website](https://trigger.dev) | [Issues](https://github.com/triggerdotdev/trigger.dev/issues) | [Docs](https://trigger.dev/docs)

[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/triggerdotdev.svg?style=social&label=Follow%20%40trigger.dev)](https://twitter.com/triggerdotdev)

</div>

# Trigger.dev Supervisor

The Supervisor is a core component of the Trigger.dev execution infrastructure. It manages worker groups and coordinates task execution in self-hosted environments.

## Package Purpose

The Supervisor provides the following functionality:

- Manages worker groups and their lifecycle
- Coordinates task distribution to workers
- Monitors worker health and performance
- Handles worker scaling based on demand
- Facilitates communication between the platform and workers
- Enforces security policies and authentication
- Reports statistics and telemetry

## Architecture

The Supervisor acts as a bridge between the Trigger.dev platform and the actual worker processes that execute tasks. It's designed to run in a containerized environment and can be deployed alongside other Trigger.dev components or as a standalone service.

```
┌───────────────┐      ┌───────────────┐      ┌───────────────┐
│               │      │               │      │  Worker 1     │
│  Trigger.dev  │◄────▶│  Supervisor   │◄────▶│  (Container)  │
│  Platform     │      │  (This App)   │      │               │
└───────────────┘      └───────────────┘      └───────────────┘
                              │
                              │               ┌───────────────┐
                              │               │  Worker 2     │
                              └──────────────▶│  (Container)  │
                                              │               │
                                              └───────────────┘
```

## Development Setup

1. Create a worker group via the API:

```sh
api_url=http://localhost:3030
wg_name=my-worker

# edit these
admin_pat=tr_pat_...
project_id=clsw6q8wz...

curl -sS \
    -X POST \
    "$api_url/admin/api/v1/workers" \
    -H "Authorization: Bearer $admin_pat" \
    -H "Content-Type: application/json" \
    -d "{
        \"name\": \"$wg_name\",
        \"makeDefault\": true,
        \"projectId\": \"$project_id\"
    }"
```

2. Create `.env` and set the worker token:

```sh
cp .env.example .env

# Then edit your .env and set this to the token.plaintext value
TRIGGER_WORKER_TOKEN=tr_wgt_...
```

3. Start the supervisor:

```sh
pnpm dev
```

4. Build the CLI, then deploy a reference project:

```sh
pnpm exec trigger deploy --self-hosted

# The additional network flag is required on linux
pnpm exec trigger deploy --self-hosted --network host
```

## Configuration Options

The Supervisor can be configured using environment variables specified in the `.env` file:

- `TRIGGER_API_URL`: URL of the Trigger.dev API
- `TRIGGER_WORKER_TOKEN`: Authentication token for the worker group
- `WORKER_CONCURRENCY`: Maximum number of concurrent tasks per worker
- `SUPERVISOR_PORT`: Port for the Supervisor to listen on
- `LOG_LEVEL`: Logging verbosity level

## Deployment

The Supervisor is designed to be deployed as a container. A Containerfile is provided for building the image:

```sh
# Build the image
docker build -f Containerfile -t trigger-supervisor .

# Run the container
docker run -p 8000:8000 \
  --env-file .env \
  trigger-supervisor
```

## Monitoring

The Supervisor exposes metrics and health check endpoints:

- `/health`: Returns the health status of the supervisor
- `/metrics`: Prometheus metrics endpoint (when configured)

## For Developers

If you're contributing to Trigger.dev, the Supervisor is a critical component for understanding how task execution is managed in self-hosted environments.
