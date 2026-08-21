# Base de Conhecimento

### Base de Conhecimento for Claude, ChatGPT and AI agents

Your private knowledge base: upload documents (.md, .txt, .docx, PDF, images), the platform indexes everything semantically and the agent retrieves the relevant context on demand. Built for firms. Each base is isolated, content stays encrypted on the platform. You pay only for what you store.

- 📊 **7 tools**
- 🔒 **Read-only**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `Base de Conhecimento`, URL `https://api.mcp.ai/p_kb`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=kb&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9rYiJ9)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=kb&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_kb%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_kb
```

---

## 7 tools

| Tool | Description |
|---|---|
| `kb_search` | Busca semântica na base de conhecimento. |
| `kb_list_documents` | Lista os documentos da base (id, nome, status, tamanho, nº de chunks). |
| `kb_get_document` | Metadados + status de um documento específico (sem o texto cru). |
| `kb_add_text` | Adiciona um texto colado à base (vira um documento indexado e buscável). |
| `kb_ingest_url` | Baixa um arquivo de uma URL (.md/.txt/.docx) e o indexa na base. |
| `kb_remove_document` | Remove um ou mais documentos da base (apaga o original, os chunks e o índice). |
| `kb_list_accounts` | Lista as bases de conhecimento conectadas neste install. |

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_kb` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
