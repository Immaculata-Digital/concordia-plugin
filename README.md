# Concordia ERP — Official AI Plugin (MCP)

Plugin oficial do **Concordia ERP** para **Claude Code**, **Claude (Web/Desktop)**, **Google Antigravity**, **OpenAI Codex** e **Cursor**.

Conecta seu agente de IA diretamente ao servidor remoto **`https://mcp.concordiaerp.com/mcp`** via **OAuth 2.1 + PKCE**, respeitando rigorosamente o isolamento multi-tenant e as permissões reais do seu usuário no Concordia ERP.

## Instalação Rápida

### Claude Code
```bash
claude mcp add --transport http concordia https://mcp.concordiaerp.com/mcp
```
Ou via plugin:
```bash
claude plugin marketplace add Immaculata-Digital/concordia-plugin
claude plugin install concordia
```

### Google Antigravity / Cursor / VS Code
Adicione ao seu `mcp_config.json`:
```json
{
  "mcpServers": {
    "concordia": {
      "serverUrl": "https://mcp.concordiaerp.com/mcp"
    }
  }
}
```

### OpenAI Codex (CLI)
```bash
codex mcp add concordia --url https://mcp.concordiaerp.com/mcp
```

## Autenticação & Segurança
Ao conectar pela primeira vez, seu agente abrirá a tela `/integracoes/conectar-mcp` no Concordia ERP para aprovação em 1 clique. Você pode gerenciar ou revogar o acesso a qualquer momento em **Integrações → API Tokens**.
