---
title: Vault curado - 07-INTEGRACOES/MCP respondio
publish: true
tags: [vault, curado]
---

# Vault curado - 07-INTEGRACOES/MCP respondio

---
tags: [integracao, mcp, ferramenta]
---
# MCP respondio (`@respond-io/mcp-server`)

Servidor MCP oficial respond.io. Usado por 09-AGENTES-CONECTADOS/Claude (eu) pra ler/escrever no 07-INTEGRACOES/respond.io space 413594.

## Config (em `~/agente-jaiane/.mcp.json`)
```json
{
  "mcpServers": {
    "respondio": {
      "command": "bash",
      "args": ["-c", "set -a; . .env; set +a; exec npx -y @respond-io/mcp-server@latest"]
    }
  }
}
```

## Tools principais
- `mcp__respondio__get_contact`
- `mcp__respondio__list_messages`
- `mcp__respondio__send_message`
- `mcp__respondio__add_contact_tags` / `remove_contact_tags`
- `mcp__respondio__update_contact_lifecycle`

## Padrão obrigatório
Identifier: `id:<contact_id>` (ex: `id:443354898`).
