# RPC Endpoints

Public RPCs for interacting with HyperEVM.

## File Format

Each provider should create one JSON file named `<entity-name>.json` with the following structure:

```json
{
  "entity": "your-entity-name",
  "endpoints": [
    {
      "name": "Provider Name",
      "url": "https://your-rpc-endpoint.com/evm",
      "description": "Brief description of your RPC service",
      "rateLimits": {
        "requests_per_second": 10,
        "requests_per_minute": 600
      }
    }
  ]
}
```

## Field Descriptions

- **entity** (required): Your entity identifier, must match the filename
- **endpoints** (required): Array of RPC endpoints you provide
  - **name** (optional): Display name for this endpoint
  - **url** (required): The full RPC endpoint URL
  - **description** (optional): Brief description of the endpoint
  - **rateLimits** (optional): Object with rate limit details
    - Can include any key-value pairs like `requests_per_second`, `requests_per_minute`, etc.

## Examples

### Simple RPC
```json
{
  "entity": "simple-provider",
  "endpoints": [
    {
      "url": "https://rpc.simple-provider.com/evm",
      "description": "Free community RPC"
    }
  ]
}
```

### Advanced RPC with Multiple Endpoints
```json
{
  "entity": "advanced-provider",
  "endpoints": [
    {
      "name": "EU Region",
      "url": "https://eu.rpc.advanced-provider.com/evm",
      "description": "European RPC endpoint with low latency",
      "rateLimits": {
        "requests_per_second": 50,
        "requests_per_minute": 2000
      }
    },
    {
      "name": "US Region",
      "url": "https://us.rpc.advanced-provider.com/evm",
      "description": "US RPC endpoint optimized for Americas",
      "rateLimits": {
        "requests_per_second": 50,
        "requests_per_minute": 2000
      }
    }
  ]
}
```

## Public Load Balancer

All community RPCs are aggregated into a single load-balanced endpoint:

`https://rpc.hyperliquid.directory/evm`

Which provides:
- Automatic failover between providers
- Geographic routing for optimal latency
- Health monitoring and automatic exclusion of failing endpoints

## Rate Limiting

Providers can specify rate limits in their endpoint configuration. Our load balancer will enforce these limits per end-user (WIP).

### L7 Proxy Considerations

Our load balancer operates as a Layer 7 proxy, terminating client connections and establishing new ones to upstream providers. This means:
- All requests to your RPC will originate from our load balancer IPs
- The original client IP is preserved in the `X-Forwarded-For` header
- To properly rate limit individual users (not our proxy), configure your infrastructure to evaluate limits based on `X-Forwarded-For`

### Load Balancer Origins

When implementing `X-Forwarded-For` based rate limiting, whitelist these hosts:
- `us-east.rpc.hyperliquid.directory`
- `eu.rpc.hyperliquid.directory`
- `tyo.rpc.hyperliquid.directory`

Feel free to [ping us](https://t.me/murakamikaze) for support on this

## Contributing

1. Add your resource
2. Run `npm run validate`
3. Submit PR