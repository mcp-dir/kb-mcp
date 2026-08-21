# Base de Conhecimento

### Base de Conhecimento para Claude, ChatGPT e agentes de IA

Sua base de conhecimento privada: suba documentos (.md, .txt, .docx, PDF, imagens), a plataforma indexa tudo semanticamente e o agente busca o contexto relevante na hora. Ideal pra escritórios. Cada base é isolada, o conteúdo fica criptografado na plataforma. Você paga só pelo que armazena.

- 📊 **7 ferramentas**
- 🔒 **Somente leitura**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Base de Conhecimento` e **URL** `https://api.mcp.ai/p_kb`.

### Cursor

[➕ Instalar Base de Conhecimento no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=kb&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9rYiJ9)

### VS Code (Copilot Chat)

[➕ Instalar Base de Conhecimento no VS Code](vscode:mcp/install?name=kb&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_kb%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_kb
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Busque na minha base: qual o prazo de rescisão do contrato padrão?
Adicione esta anotação à base de conhecimento
Liste os documentos da minha base
```

---

## 7 ferramentas disponíveis

| Tool | Descrição |
|---|---|
| `kb_search` | Busca semântica na base de conhecimento. |
| `kb_list_documents` | Lista os documentos da base (id, nome, status, tamanho, nº de chunks). |
| `kb_get_document` | Metadados + status de um documento específico (sem o texto cru). |
| `kb_add_text` | Adiciona um texto colado à base (vira um documento indexado e buscável). |
| `kb_ingest_url` | Baixa um arquivo de uma URL (.md/.txt/.docx) e o indexa na base. |
| `kb_remove_document` | Remove um ou mais documentos da base (apaga o original, os chunks e o índice). |
| `kb_list_accounts` | Lista as bases de conhecimento conectadas neste install. |

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Somente leitura**, nenhuma ferramenta altera dados na origem.
- **Sub-processadores**: OpenAI, o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_kb`.


---

## Suporte

- 📧 [kb@mcp.ai](mailto:kb@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/kb-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_kb` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
