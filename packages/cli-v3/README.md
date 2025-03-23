<div align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
  <source media="(prefers-color-scheme: light)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/3f5ad4c1-c4c8-4277-b622-290e7f37bd00/public">
  <img alt="Trigger.dev logo" src="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
</picture>
  
### Command Line Interface for Trigger.dev

[Discord](https://trigger.dev/discord) | [Website](https://trigger.dev) | [Issues](https://github.com/triggerdotdev/trigger.dev/issues) | [Docs](https://trigger.dev/docs)

[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/triggerdotdev.svg?style=social&label=Follow%20%40trigger.dev)](https://twitter.com/triggerdotdev)

</div>

# trigger.dev CLI (v3)

The Trigger.dev CLI is a command-line tool that helps you develop, test, and deploy Trigger.dev applications.

## Package Purpose

The CLI provides a set of commands for:

- Initializing new Trigger.dev projects
- Developing tasks locally with hot-reloading
- Testing task execution
- Managing deployments
- Connecting to the Trigger.dev cloud or self-hosted instances
- Generating code and configuration files
- Viewing logs and monitoring task execution

## Key Features

- **Project Setup**: Initialize new projects with the right configuration
- **Dev Mode**: Run a local development server that automatically reloads tasks
- **Testing Tools**: Test tasks locally before deployment
- **Deployment Management**: Handle task deployments to production
- **Authentication**: Manage API keys and authentication
- **Log Viewing**: Stream logs from running tasks
- **Project Configuration**: Manage project settings and environment variables
- **Code Generation**: Scaffold new tasks and integrations

## Installation

```bash
# Install globally
npm install -g trigger.dev

# Or use npx without installing
npx trigger.dev@latest init
```

## Common Commands

```bash
# Initialize a new project
trigger init

# Start the dev server
trigger dev

# Test a specific task
trigger test my-task

# Deploy tasks
trigger deploy

# Check status
trigger status

# Login to Trigger.dev
trigger login

# View logs
trigger logs
```

## Configuration

The CLI reads configuration from:

- A `trigger.config.ts` or `trigger.config.js` file in your project
- Environment variables
- Command line arguments

## Project Integration

The CLI works with various frameworks and project types:

- Next.js
- Express
- Remix
- Serverless
- Standalone Node.js applications

## Dependencies

- Node.js v18.20.0 or higher
- Various build tools for different project types
- OpenTelemetry for tracing and metrics

## For Developers

The CLI is a crucial tool for the Trigger.dev development workflow, making it easy to create, test, and deploy background tasks in your applications.

# Trigger.dev CLI

A CLI that allows you to create, run locally and deploy Trigger.dev background tasks.

Note: this only works with Trigger.dev v3 projects and later. For older projects use the [@trigger.dev/cli](https://www.npmjs.com/package/@trigger.dev/cli) package.

Trigger.dev is an open source platform that makes it easy to create event-driven background tasks directly in your existing project.

## Commands

| Command                                                              | Description                                                        |
| :------------------------------------------------------------------- | :----------------------------------------------------------------- |
| [login](https://trigger.dev/docs/cli-login-commands)                 | Login with Trigger.dev so you can perform authenticated actions.   |
| [init](https://trigger.dev/docs/cli-init-commands)                   | Initialize your existing project for development with Trigger.dev. |
| [dev](https://trigger.dev/docs/cli-dev-commands)                     | Run your Trigger.dev tasks locally.                                |
| [deploy](https://trigger.dev/docs/cli-deploy-commands)               | Deploy your Trigger.dev v3 project to the cloud.                   |
| [whoami](https://trigger.dev/docs/cli-whoami-commands)               | Display the current logged in user and project details.            |
| [logout](https://trigger.dev/docs/cli-logout-commands)               | Logout of Trigger.dev.                                             |
| [list-profiles](https://trigger.dev/docs/cli-list-profiles-commands) | List all of your CLI profiles.                                     |
| [update](https://trigger.dev/docs/cli-update-commands)               | Updates all `@trigger.dev/*` packages to match the CLI version.    |

## MCP Server

The [Model Context Protocol (MCP)](https://modelcontextprotocol.io/introduction) is an open protocol that allows you to provide custom tools
to agentic LLM clients, like [Claude for Desktop](https://docs.anthropic.com/en/docs/claude-for-desktop/overview), [Cursor](https://www.cursor.com/), [Windsurf](https://windsurf.com/), etc...

The Trigger.dev CLI can expose an MCP server and enable you interact with Trigger.dev in agentic LLM workflows. For example, you can use
it to trigger tasks via natural language, view task runs, view logs, debug issues with task runs, etc...

### Starting the Trigger.dev MCP Server

To start the Trigger.dev MCP server, simply pass the `--mcp` flag to the `dev` command:

```bash
trigger dev --mcp
```

By default it runs on port `3333`. You can change this by passing the `--mcp-port` flag:

```bash
trigger dev --mcp --mcp-port 3334
```

### Configuring your MCP client

This depends on what tool you are using. For Cursor, the configuration is in the [.cursor/mcp.json](../../.cursor/mcp.json) file
and should be good to go as long as you use the default MCP server port.

Check out [Cursor's docs](https://docs.cursor.com/context/model-context-protocol) for further details.

Tip: try out [Cursor's YOLO mode](https://docs.cursor.com/context/model-context-protocol#yolo-mode) for a seamless experience :D

## Support

If you have any questions, please reach out to us on [Discord](https://trigger.dev/discord) and we'll be happy to help.
