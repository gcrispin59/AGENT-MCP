# API Reference

## Core Components

### BaseAgent
The foundation for all agent implementations.

```javascript
const { BaseAgent } = require('agent-mcp');

class MyAgent extends BaseAgent {
    constructor(config) {
        super({
            type: 'custom',
            capabilities: ['feature1', 'feature2']
        });
    }
}
```

[Learn more about BaseAgent](./base-agent.html)

### EthicsAgent
Specialized agent for ethical evaluation and compliance.

```javascript
const { EthicsAgent } = require('agent-mcp');

const ethics = new EthicsAgent({
    rulesPath: './rules.json'
});
```

[Learn more about EthicsAgent](./ethics-agent.html)

### LibraryAgent
Knowledge management and information organization.

```javascript
const { LibraryAgent } = require('agent-mcp');

const library = new LibraryAgent({
    storageConfig: { type: 'distributed' }
});
```

[Learn more about LibraryAgent](./library-agent.html)

## API Endpoints

### Agent Management
- `POST /api/agents` - Create new agent
- `GET /api/agents/:id` - Get agent details
- `PUT /api/agents/:id` - Update agent
- `DELETE /api/agents/:id` - Remove agent

### Task Management
- `POST /api/tasks` - Create task
- `GET /api/tasks/:id` - Get task status
- `PUT /api/tasks/:id` - Update task
- `DELETE /api/tasks/:id` - Cancel task

## Events

### Agent Events
- `agent:ready` - Agent initialized and ready
- `agent:error` - Agent encountered an error
- `agent:task` - Agent received a task
- `agent:complete` - Agent completed a task

### System Events
- `system:ready` - System initialized
- `system:error` - System error occurred
- `system:shutdown` - System shutting down