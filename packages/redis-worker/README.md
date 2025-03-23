<div align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
  <source media="(prefers-color-scheme: light)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/3f5ad4c1-c4c8-4277-b622-290e7f37bd00/public">
  <img alt="Trigger.dev logo" src="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
</picture>
  
### Redis Worker for Trigger.dev

[Discord](https://trigger.dev/discord) | [Website](https://trigger.dev) | [Issues](https://github.com/triggerdotdev/trigger.dev/issues) | [Docs](https://trigger.dev/docs)

[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/triggerdotdev.svg?style=social&label=Follow%20%40trigger.dev)](https://twitter.com/triggerdotdev)

</div>

# @trigger.dev/redis-worker

This package provides a Redis-based worker implementation for the Trigger.dev platform, enabling distributed job processing and task execution.

## Package Purpose

The Redis Worker is a key component in the Trigger.dev infrastructure that:

- Manages job queues using Redis as a backend
- Handles job distribution across multiple worker instances
- Processes background tasks with configurable concurrency
- Provides reliable job execution with retries and error handling
- Scales horizontally for increased throughput

## Key Features

- **Redis-backed queues**: Reliable and persistent job storage
- **Distributed processing**: Run multiple workers across different machines
- **Concurrency controls**: Limit parallel job execution
- **Retry mechanism**: Automatically retry failed jobs
- **Dead letter queues**: Store failed jobs for inspection
- **Metrics**: Track job processing performance
- **Scalability**: Handle high volumes of jobs efficiently

## Architecture

The Redis Worker connects to Redis for job storage and distribution. It uses a polling mechanism to check for new jobs, processes them according to their configuration, and reports results back to the central Trigger.dev system.

```
┌────────────┐     ┌─────────┐     ┌──────────────┐
│  Job       │     │  Redis  │     │  Worker 1    │
│  Producer  │────▶│  Queue  │◀───▶│  (This pkg)  │
└────────────┘     └─────────┘     └──────────────┘
                        ▲                
                        │           ┌──────────────┐
                        └──────────▶│  Worker 2    │
                                    │  (This pkg)  │
                                    └──────────────┘
```

## Usage

This package is typically used as part of the Trigger.dev platform infrastructure rather than being directly imported by end users.

```typescript
import { createWorker } from "@trigger.dev/redis-worker";

const worker = createWorker({
  redis: redisClient,
  concurrency: 10,
  pollInterval: 1000,
});

await worker.start();
```

## Installation

```bash
npm install @trigger.dev/redis-worker
```

## Dependencies

- Redis for queue storage and job distribution
- Prometheus client for metrics
- nanoid for ID generation
- p-limit for concurrency control

## For Developers

If you're contributing to the Trigger.dev platform, this package is essential for understanding the job execution flow and distributed processing architecture.
