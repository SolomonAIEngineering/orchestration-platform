<div align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
  <source media="(prefers-color-scheme: light)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/3f5ad4c1-c4c8-4277-b622-290e7f37bd00/public">
  <img alt="Trigger.dev logo" src="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
</picture>
  
### Core Package for Trigger.dev

[Discord](https://trigger.dev/discord) | [Website](https://trigger.dev) | [Issues](https://github.com/triggerdotdev/trigger.dev/issues) | [Docs](https://trigger.dev/docs)

[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/triggerdotdev.svg?style=social&label=Follow%20%40trigger.dev)](https://twitter.com/triggerdotdev)

</div>

# @trigger.dev/core

This package contains core code and shared utilities used across the Trigger.dev SDK and platform.

## Package Purpose

The core package provides essential functionality, types, and utilities that are shared between the SDK and the platform's backend services. It acts as the foundational layer for the Trigger.dev ecosystem, including:

- Common types and interfaces
- Shared schemas and validators
- Utility functions and helpers
- Tracing and logging infrastructure
- Error handling mechanisms
- Communication protocols

## Key Components

- **Schema definitions**: Zod schemas for validating data structures
- **Logging**: Structured logging utilities
- **Tracing**: OpenTelemetry integration for distributed tracing
- **Error handling**: Standard error classes and handling patterns
- **Utilities**: Common helper functions used across the platform
- **Types**: TypeScript types and interfaces shared between packages

## Usage

This package is primarily used internally by other Trigger.dev packages. It's not typically imported directly by end users, but rather serves as a foundation for the rest of the platform.

```typescript
import { zodNamespace } from "@trigger.dev/core/v3/zodNamespace";
import { type SpanAttributes } from "@trigger.dev/core/v3/types";
```

## Installation

```bash
npm install @trigger.dev/core
```

## Dependencies

This package integrates with:

- OpenTelemetry for tracing and logging
- Zod for schema validation
- Socket.io for real-time communication
- TypeScript for type safety

## For Developers

If you're contributing to the Trigger.dev platform, understanding this package is essential as it provides the fundamental building blocks used throughout the codebase. 