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

## Best Practices

1. **Performance**: Ensure fast loading times and responsive UI
2. **Features**: Provide comprehensive blockchain data (blocks, txs, validators)
3. **Search**: Implement robust search functionality
4. **Mobile**: Optimize for mobile devices
5. **API**: Consider offering an API for programmatic access

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

## Common Features

Good explorers typically include:
- Block details and history
- Transaction search and details
- Address/account information
- Validator information and voting power
- Network statistics
- Token transfers and balances
- Smart contract verification
- API documentation

## Contributing

1. Fork
2. Add your resource: `explorers/your-entity.json`
3. Pass validation: `npm run validate`
4. Submit a PR 