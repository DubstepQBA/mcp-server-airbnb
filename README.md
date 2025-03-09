# Airbnb MCP Server

MCP Server for Airbnb search and listing details.

## Tools

1. `airbnb_search`
   - Search for Airbnb listings
   - Required Input: `location` (string)
   - Optional Inputs:
     - `placeId` (string)
     - `checkin` (string, YYYY-MM-DD)
     - `checkout` (string, YYYY-MM-DD)
     - `adults` (number)
     - `children` (number)
     - `infants` (number)
     - `pets` (number)
     - `minPrice` (number)
     - `maxPrice` (number)
     - `cursor` (string)
     - `ignoreRobotsText` (boolean)
   - Returns: Array of listings with details like name, price, location, etc.

2. `airbnb_listing_details`
   - Get detailed information about a specific Airbnb listing
   - Required Input: `id` (string)
   - Optional Inputs:
     - `checkin` (string, YYYY-MM-DD)
     - `checkout` (string, YYYY-MM-DD)
     - `adults` (number)
     - `children` (number)
     - `infants` (number)
     - `pets` (number)
     - `ignoreRobotsText` (boolean)
   - Returns: Detailed listing information including description, host details, amenities, pricing, etc.

## Features

- Respects Airbnb's robots.txt rules
- Uses cheerio for HTML parsing
- No API key required
- Returns structured JSON data
- Reduces context load by flattening and picking data

## Setup

### Usage with Claude Desktop
1. Go to: Settings > Developer > Edit Config

2. Add the following to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "airbnb": {
      "command": "npx",
      "args": [
        "-y",
        "@openbnb/mcp-server-airbnb"
      ]
    }
  }
}
```

To ignore robots.txt for all requests, use this version with `--ignore-robots-txt` args

```json
{
  "mcpServers": {
    "airbnb": {
      "command": "npx",
      "args": [
        "-y",
        "@openbnb/mcp-server-airbnb",
        "--ignore-robots-txt"
      ]
    }
  }
}
```
3. Restart Claude Desktop and plan your next trip that include Airbnbs!

## Build (for devs)

```bash
npm install
npm run build
```

## License

This MCP server is licensed under the MIT License.

## Disclaimer

Airbnb is a trademark of Airbnb, Inc.
OpenBnB is not Not related to Airbnb, Inc. or its subsidiaries

