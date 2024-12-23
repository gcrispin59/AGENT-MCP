# Simple Agent Example

This example demonstrates how to create and use a basic agent in the AGENT MCP system.

## Code Example

```javascript
const { BaseAgent } = require('agent-mcp');

class SimpleAgent extends BaseAgent {
    constructor() {
        super({
            type: 'basic',
            capabilities: ['processing']
        });
    }

    async processTask(task) {
        this.logger.info('Processing task', { taskId: task.id });
        
        // Simple task processing logic
        const result = {
            taskId: task.id,
            status: 'completed',
            result: `Processed ${task.data}`
        };

        return result;
    }
}

// Usage
async function main() {
    const agent = new SimpleAgent();
    await agent.initialize();

    // Handle task
    const task = {
        id: '123',
        type: 'processing',
        data: 'example data'
    };

    const result = await agent.handleTask(task);
    console.log('Task result:', result);
}

main().catch(console.error);
```

## Explanation

1. We extend `BaseAgent` to create our custom agent
2. We define basic capabilities in the constructor
3. We implement the `processTask` method
4. We initialize the agent and handle tasks

## Next Steps

- Add error handling
- Implement more capabilities
- Add state management
- Configure logging