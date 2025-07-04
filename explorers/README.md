# Block Explorers

Hyperliquid blockchain explorers for viewing transactions, blocks, and network activity.

## File Format

Each explorer should create one JSON file named `<entity-name>.json` with the following structure:

```json
{
  "entity": "your-entity-name",
  "url": "https://your-explorer.com",
  "description": "Description of your explorer"
}
```

## Field Descriptions

- **entity** (required): Your entity identifier, must match the filename
- **url** (required): The explorer website URL
- **description** (required): Brief description of what your explorer offers

## Examples

### Basic Explorer
```json
{
  "entity": "basic-explorer",
  "url": "https://explorer.basic.com",
  "description": "Simple Hyperliquid blockchain explorer"
}
```

### Advanced Explorer
```json
{
  "entity": "advanced-explorer",
  "url": "https://hyperscan.pro",
  "description": "Advanced explorer with DeFi analytics, validator metrics, and API access"
}
```

## Contributing

1. Fork
2. Add your resource: `explorers/your-entity.json`
3. Pass validation: `npm run validate`
4. Submit a PR 