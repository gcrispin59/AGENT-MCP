# LibraryAgent API Reference

## Overview

The LibraryAgent manages knowledge organization, information retrieval, and semantic tagging within the AGENT MCP system. It provides sophisticated capabilities for information management and discovery.

## Constructor

```javascript
constructor(config: LibraryAgentConfig)
```

### Parameters

```typescript
interface LibraryAgentConfig {
    storageConfig: StorageConfig;    // Storage configuration
    indexingConfig?: IndexConfig;    // Optional: Indexing settings
    semanticConfig?: SemanticConfig; // Optional: Semantic analysis settings
}
```

## Methods

### gatherInformation()
```javascript
async gatherInformation(query: SearchQuery): Promise<SearchResults>
```
Searches and retrieves relevant information.

### evaluateSource()
```javascript
async evaluateSource(source: Source): Promise<SourceEvaluation>
```
Evaluates the credibility and relevance of information sources.

### organizeKnowledge()
```javascript
async organizeKnowledge(content: Content): Promise<KnowledgeStructure>
```
Organizes and categorizes information.

### createSemanticTags()
```javascript
async createSemanticTags(content: Content): Promise<SemanticTags>
```
Generates semantic tags and relationships.

### createCrossReferences()
```javascript
async createCrossReferences(content: Content): Promise<CrossReferences>
```
Identifies and creates links between related information.

## Events

- `search:complete`: Information gathering completed
- `source:evaluated`: Source evaluation completed
- `knowledge:organized`: Knowledge organization completed
- `tags:created`: Semantic tagging completed

## Example Usage

```javascript
const libraryAgent = new LibraryAgent({
    storageConfig: {
        type: 'distributed',
        persistence: true
    }
});

// Search for information
const results = await libraryAgent.handleTask({
    type: 'gather_information',
    data: {
        query: 'advanced machine learning techniques',
        depth: 'deep',
        sources: ['academic', 'research_papers']
    }
});

// Handle results
libraryAgent.on('search:complete', (results) => {
    console.log('Found sources:', results.length);
    results.forEach(result => {
        console.log('Source:', result.title);
        console.log('Relevance:', result.relevance);
        console.log('Tags:', result.semanticTags);
    });
});
```

## Response Types

### SearchResults
```typescript
interface SearchResults {
    results: SearchResult[];
    metadata: {
        query: string;
        timestamp: Date;
        source_count: number;
    }
}
```

### SourceEvaluation
```typescript
interface SourceEvaluation {
    reliability_score: number;
    authenticity_score: number;
    relevance_score: number;
    quality_metrics: QualityMetrics;
    recommendations: string[];
}
```

## Best Practices

1. Regular index maintenance
2. Cache management
3. Source verification
4. Semantic enrichment
5. Cross-reference validation