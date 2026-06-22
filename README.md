# ai-project-architect

## GitHub MCP setup

### Files

- `.env.example`
- `.mcp.json`
- `docker-compose.yml`
- `.gitignore`

Add your GitHub token.

1. Copy `.env.example` to `.env`.
2. Put your GitHub token in `.env`.

```env
GITHUB_TOKEN=your_github_token_here
```

### MCP configuration

`.mcp.json` contains:

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "github-mcp-server"],
      "env": {
        "GITHUB_TOKEN": "${GITHUB_TOKEN}"
      }
    }
  }
}
```

### Run the project in Docker

```bash
docker compose up --build
```

### What should run

- `docker-compose.yml` starts the app container.
- Inside the container:
  - `npm install`.
  - `npm run build`.
- `.mcp.json` tells the client to start the GitHub MCP server with `npx`.
- `GITHUB_TOKEN` is read from `.env`.

### Expected result

- The project builds successfully.
- The GitHub MCP server can authenticate using your token.
- The environment is ready for GitHub-related MCP actions.
