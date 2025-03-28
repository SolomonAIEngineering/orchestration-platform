<div align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
  <source media="(prefers-color-scheme: light)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/3f5ad4c1-c4c8-4277-b622-290e7f37bd00/public">
  <img alt="Trigger.dev logo" src="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
</picture>
  
### Open source background jobs with no timeouts

[Discord](https://trigger.dev/discord) | [Website](https://trigger.dev) | [Issues](https://github.com/triggerdotdev/trigger.dev/issues) | [Docs](https://trigger.dev/docs)

[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/triggerdotdev.svg?style=social&label=Follow%20%40trigger.dev)](https://twitter.com/triggerdotdev)

</div>

# Official TypeScript SDK for Trigger.dev

The Trigger.dev SDK is a TypeScript/JavaScript library that allows you to define and trigger tasks in your project.

## About

Trigger.dev is an open source platform and SDK which allows you to create long-running background jobs. Write normal async code, deploy, and never hit a timeout.

## Package Purpose

This package provides the primary SDK interface for developers to:

- Define tasks that can run without timeouts
- Set up triggers based on events, schedules, or webhooks
- Configure retries, concurrency, and other job parameters
- Connect to integrations and APIs
- Monitor and track task executions
- Stream logs and results
- Control job execution flow

It's designed to be used in your application code to define background tasks that will be executed by the Trigger.dev platform.

## Key Features

- **Task Definition**: Create tasks with unique IDs and run functions
- **Timeout-Free Execution**: Run code that takes longer than typical serverless timeouts
- **Retry Handling**: Built-in exponential backoff and configurable retry policies
- **Scheduled Tasks**: Cron expressions and interval-based scheduling
- **Event-Driven Triggers**: React to events from integrations or webhooks
- **Observability**: Track execution progress and status
- **TypeScript Support**: Full type safety for your task definitions

## Installation

```bash
npm install @trigger.dev/sdk
```

## Getting started

The quickest way to get started is to create an account in our [web app](https://cloud.trigger.dev), create a new project and follow the instructions in the onboarding. Build and deploy your first task in minutes.

## SDK usage

For more information on our SDK, refer to our [docs](https://trigger.dev/docs/introduction).

## Support

If you have any questions, please reach out to us on [Discord](https://trigger.dev/discord) and we'll be happy to help.
