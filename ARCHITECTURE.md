# Trigger.dev Platform Architecture

## Overview

Trigger.dev is an open-source platform for building and running background tasks, workflows, and scheduled jobs. It allows developers to write long-running tasks in TypeScript/JavaScript without hitting timeouts, with built-in retries, observability, and scaling.

## Repository Structure

The codebase is organized as a monorepo with several key directories:

- `packages/`: Main public packages that users interact with
- `internal-packages/`: Platform infrastructure components
- `apps/`: User-facing applications and services
- `scripts/`: Development and CI scripts
- `tests/`: End-to-end and integration tests

## Key Components

### Public Packages

1. **@trigger.dev/sdk** (packages/trigger-sdk)
   - Main SDK for defining tasks and triggers
   - Task execution, lifecycle management, and retries
   - Integration with various APIs and services

2. **@trigger.dev/core** (packages/core)
   - Shared utilities, types, and infrastructure
   - Base schemas and validation logic
   - Logging and tracing functionality

3. **@trigger.dev/react-hooks** (packages/react-hooks)
   - React hooks for displaying task status in UI
   - Task triggering from frontend applications
   - Real-time updates and streaming

4. **@trigger.dev/redis-worker** (packages/redis-worker)
   - Redis-based queue and worker implementation
   - Job distribution and execution infrastructure
   - Concurrency controls and scheduling

5. **trigger.dev CLI** (packages/cli-v3)
   - Command-line interface for development and deployment
   - Project initialization and configuration
   - Local development server and testing

### Applications

1. **Webapp** (apps/webapp)
   - Main web interface for task management
   - Built with Remix
   - Task monitoring, debugging, and configuration

2. **Supervisor** (apps/supervisor)
   - Manages worker groups for task execution
   - Coordinates task distribution
   - Health monitoring and scaling

### Internal Infrastructure

1. **Database** (internal-packages/database)
   - Prisma-based database schema and client
   - Data models for platform entities
   - Migration management

2. **Tracing** (internal-packages/tracing)
   - OpenTelemetry integration for distributed tracing
   - Metrics collection and observability
   - Error tracking and debugging

3. **Run Engine** (internal-packages/run-engine)
   - Task execution engine and runtime
   - State management and persistence
   - Error handling and retries

## Data Flow

1. A task is defined using the SDK and registered with the platform.
2. The task is triggered via an API call, webhook, or schedule.
3. The webapp enqueues the task in Redis.
4. A worker picks up the task and executes it.
5. Execution status, logs, and results are stored in the database.
6. The webapp displays real-time status and results.

## Development Process

The platform uses:
- PNPM for package management
- Turborepo for build caching and pipeline management
- TypeScript for type safety
- Prisma for database access
- Docker for containerization
- OpenTelemetry for observability

## Deployment Options

1. **Trigger.dev Cloud** - Fully managed service
2. **Self-hosted** - Deploy on your own infrastructure
   - Docker-based deployment
   - Kubernetes deployment

## Contributing

To contribute to the platform:
1. Set up the development environment
2. Make changes to relevant packages
3. Write tests for new functionality
4. Submit a pull request

Refer to the [CONTRIBUTING.md](./CONTRIBUTING.md) file for detailed instructions. 