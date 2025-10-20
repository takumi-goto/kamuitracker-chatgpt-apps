# KamuiTracker ChatGPT Apps

ChatGPT App for KamuiTracker API with MCP (Model Context Protocol) integration.

## Overview

This ChatGPT app integrates with KamuiTracker via MCP servers to provide:
- **KamuiTracker MCP**: Access to KamuiTracker API (channel search, video search, video reports)
- **Chrome DevTools MCP** (optional): Browser automation for retrieving authentication tickets

## Prerequisites

- Node.js 18+
- pnpm (recommended) or npm/yarn
- Docker (for running KamuiTracker MCP server)

## Setup

### 1. Install dependencies

```bash
pnpm install
```

### 2. Build the UI components

```bash
pnpm run build
```

This generates static assets in the `assets/` directory.

### 3. Serve the assets locally

```bash
pnpm run serve
```

Assets will be available at `http://localhost:4444` with CORS enabled.

## MCP Server Configuration

### KamuiTracker MCP Server

The KamuiTracker MCP server should be running and accessible. By default, it runs on:
- **HTTP/SSE mode**: `http://localhost:8000/mcp`

To start the KamuiTracker MCP server:

```bash
cd /path/to/kamuitracker-mcp-server
docker run --rm -p 8000:8000 kamuitracker-mcp-server
```

### ChatGPT App Configuration

Configure MCP servers in your ChatGPT app settings:

```json
{
  "mcp_servers": {
    "kamuitracker": {
      "url": "http://localhost:8000/mcp"
    }
  }
}
```

## Authentication Flow

1. Login to KamuiTracker in your browser: `https://app.kamuitracker.com/`
2. Open DevTools Console and run: `localStorage.getItem("ticket")`
3. Copy the ticket value
4. In ChatGPT, say: "Set this ticket: [paste ticket here]"
5. You can now use all KamuiTracker features

## Available Features

- **Channel Search**: Search YouTube channels with various filters
- **Video Search**: Search videos with advanced filtering
- **Video Reports**: Access detailed analytics and comment analysis

## Development

Run the Vite dev server for live reloading:

```bash
pnpm run dev
```

## License

MIT
