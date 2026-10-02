# TripWays MCP connector

[![TripWays MCP connector](https://glama.ai/mcp/connectors/com.tripways/tours/badges/score.svg)](https://glama.ai/mcp/connectors/com.tripways/tours)

Connect your AI assistant to [TripWays](https://tripways.com/mcp/): about 16,000 tours, day trips and activities in 120 countries. Ask in plain words, check live dates and seats, get the real price for your group, and open a TripWays checkout link with your date, time and travelers filled in.

- **Server:** `https://mcp.tripways.com/mcp` (Streamable HTTP)
- **Sign-in:** none. Public catalog data.
- **Read-only:** it never holds a seat, creates a cart or takes a card. You pay on tripways.com.
- **Registry name:** `com.tripways/tours`

This repository holds only connection files. The server itself is run by TripWays.

## Connect

### Claude (claude.ai, desktop, mobile)

Open the [TripWays page in the Claude directory](https://claude.ai/directory/mcp-tripways-com) and add it. Or: **Settings → Connectors → Add custom connector**, URL `https://mcp.tripways.com/mcp`, leave sign-in empty.

### ChatGPT

Use the TripWays app once it appears in the ChatGPT app directory. Until then, with developer mode on: **Settings → Connectors → Create**, URL `https://mcp.tripways.com/mcp`, authentication **None**.

### Claude Code

```bash
claude mcp add --transport http tripways https://mcp.tripways.com/mcp
```

Or install it as a plugin from this repository's marketplace:

```bash
claude plugin marketplace add allseen-com/tripways-mcp-connect
claude plugin install tripways@tripways
```

### Cursor

[Add TripWays to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=tripways&config=eyJ1cmwiOiJodHRwczovL21jcC50cmlwd2F5cy5jb20vbWNwIn0=)

Or add it to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "tripways": { "url": "https://mcp.tripways.com/mcp" }
  }
}
```

### Gemini CLI

```bash
gemini extensions install https://github.com/allseen-com/tripways-mcp-connect
```

Or add the server only:

```bash
gemini mcp add --transport http tripways https://mcp.tripways.com/mcp
```

### Any other MCP client

Streamable HTTP, URL `https://mcp.tripways.com/mcp`, no authentication. The registry entry is [`server.json`](server.json).

## Tools

All six are read-only.

| Tool | What it does |
|------|--------------|
| `search_tours` | Search by place, budget, duration, activity and cancellation policy. |
| `get_tour_details` | Itinerary, inclusions, meeting point, cancellation terms. |
| `get_destination_info` | Resolve a place name (for example "Khao Sok") to a destination. |
| `check_availability` | Open dates, start times and seats from the operator's live calendar. |
| `get_price_quote` | The USD total for your group on a date and start time. A quote, not a hold. |
| `get_booking_link` | A tripways.com checkout link with date, time and travelers filled in. |

## Example prompts

- Find a food tour in Rome under $100.
- What is included on the Phang Nga Bay sunset dinner cruise (tour 1016530)?
- Is there space for 2 adults on tour 1016530 between 10 and 16 November 2026?
- How much is that for 2 adults on 13 November at the first start time?
- Give me the TripWays booking link for that.

## Privacy and support

The connector receives only each tool's arguments (search text, filters, tour id, dates, traveler counts). It never asks for your conversation, name, email or location. See [section 3D of the privacy policy](https://tripways.com/privacy-policy/).

- Guide and help: https://tripways.com/mcp/
- Support: info@tripways.com
- Company: All Seen LLC (TripWays.com)

## License

MIT, for the files in this repository.
