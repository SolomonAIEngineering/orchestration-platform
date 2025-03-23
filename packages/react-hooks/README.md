<div align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
  <source media="(prefers-color-scheme: light)" srcset="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/3f5ad4c1-c4c8-4277-b622-290e7f37bd00/public">
  <img alt="Trigger.dev logo" src="https://imagedelivery.net/3TbraffuDZ4aEf8KWOmI_w/a45d1fa2-0ae8-4a39-4409-f4f934bfae00/public">
</picture>
  
### React Hooks for Trigger.dev

[Discord](https://trigger.dev/discord) | [Website](https://trigger.dev) | [Issues](https://github.com/triggerdotdev/trigger.dev/issues) | [Docs](https://trigger.dev/docs)

[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/triggerdotdev.svg?style=social&label=Follow%20%40trigger.dev)](https://twitter.com/triggerdotdev)

</div>

# @trigger.dev/react-hooks

This package provides React hooks for integrating with Trigger.dev in frontend applications, allowing you to interact with background tasks and display their status in your UI.

## Package Purpose

The React Hooks package enables frontend developers to:

- Trigger background tasks from React applications
- Display the status and progress of running tasks
- Stream real-time updates from long-running processes
- Fetch and display task metadata and results
- Create interactive UI components tied to background jobs

## Key Features

- **Task Triggering**: Start background tasks from your React UI
- **Status Tracking**: Monitor task progress and completion status
- **Real-time Updates**: Receive live updates as tasks progress
- **Error Handling**: Display job failures and retry capabilities
- **Result Fetching**: Retrieve and display task results
- **Type Safety**: Full TypeScript support for task parameters and results

## Usage Examples

### Triggering a Task

```tsx
import { useTriggerTask } from "@trigger.dev/react-hooks";

function SubmitButton() {
  const { trigger, isLoading, error } = useTriggerTask("generate-report");
  
  return (
    <button 
      onClick={() => trigger({ reportType: "monthly" })}
      disabled={isLoading}
    >
      {isLoading ? "Generating..." : "Generate Report"}
      {error && <div className="error">{error.message}</div>}
    </button>
  );
}
```

### Displaying Task Status

```tsx
import { useTaskStatus } from "@trigger.dev/react-hooks";

function TaskStatus({ taskId }) {
  const { status, progress, result } = useTaskStatus(taskId);
  
  if (status === "completed") {
    return <div>Task completed: {JSON.stringify(result)}</div>;
  }
  
  if (status === "running") {
    return <div>Running... {progress}%</div>;
  }
  
  return <div>Waiting to start...</div>;
}
```

## Installation

```bash
npm install @trigger.dev/react-hooks
```

## Dependencies

- React 18 or newer
- SWR for data fetching and caching
- @trigger.dev/core for shared types and utilities

## Compatibility

Works with all modern React frameworks, including:

- Next.js
- Create React App
- Remix
- Vite-based applications

## For Developers

These hooks provide the frontend integration points for your Trigger.dev tasks, making it easy to create interactive UIs that leverage background processing.
