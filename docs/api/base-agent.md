# BaseAgent API Reference

## Overview

The BaseAgent class serves as the foundation for all agent implementations in the AGENT MCP system. It provides core functionality for task handling, state management, and agent communication.

## Constructor

```javascript
constructor(config: AgentConfig)
```

### Parameters

```typescript
interface AgentConfig {
    id?: string;              // Optional: Unique identifier
    type: string;             // Required: Agent type
    capabilities: string[];   // Required: List of capabilities
    resources?: ResourceSpec; // Optional: Resource requirements
}
```

## Methods

### initialize()
```javascript
async initialize(): Promise<void>
```
Initializes the agent and connects to the MCP system.

### handleTask()
```javascript
async handleTask(task: Task): Promise<TaskResult>
```
Processes a task and returns the result.

### shutdown()
```javascript
async shutdown(): Promise<void>
```
Gracefully shuts down the agent.

## Events

- `ready`: Agent is initialized and ready
- `error`: Agent encountered an error
- `task`: Agent received a task
- `complete`: Agent completed a task

## Example Usage

```javascript
class CustomAgent extends BaseAgent {
    constructor() {
        super({
            type: 'custom',
            capabilities: ['feature1', 'feature2']
        });
    }

    async processTask(task) {
        // Implement custom task processing
        return { status: 'completed', result: {} };
    }
}

const agent = new CustomAgent();
await agent.initialize();

agent.on('ready', () => {
    console.log('Agent ready:', agent.id);
});
```

## Error Handling

```javascript
agent.on('error', (error) => {
    console.error('Agent error:', error);
    // Implement error recovery logic
});
```

## Best Practices

1. Always implement error handling
2. Override processTask() for custom behavior
3. Clean up resources in shutdown()
4. Use type-safe capabilities
5. Implement proper logging