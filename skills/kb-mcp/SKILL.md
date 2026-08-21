---
name: kb-mcp
description: Skill da REST API do Base de Conhecimento na MCP.AI: 7 endpoints em /api/kb. Sua base de conhecimento privada: suba documentos (.md, .txt, .docx, PDF, imagens), a plataforma indexa tudo semanticamente e o agente busca o contexto relevante na hora. Ideal pra escritórios. Cada base é isolada, o conteúdo fica criptografado na plataforma. Você paga só pelo que armazena. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Base de Conhecimento — REST API skill

Você tem acesso à **Base de Conhecimento** REST API na MCP.AI.

> Sua base de conhecimento privada: suba documentos (.md, .txt, .docx, PDF, imagens), a plataforma indexa tudo semanticamente e o agente busca o contexto relevante na hora. Ideal pra escritórios. Cada base é isolada, o conteúdo fica criptografado na plataforma. Você paga só pelo que armazena.

## Base URL

```
https://api.mcp.ai/api/kb
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/kb/add/text \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"title":"...","text":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/kb/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (7)

#### `kb_add_text`

Adiciona um texto colado à base (vira um documento indexado e buscável). _(POST /api/kb/add/text)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `title` | string | Sim | Título do documento. |
| `text` | string | Sim | O conteúdo de texto a indexar. |
| `account` | string | Não | Seletor opcional da base de conhecimento quando há mais de uma conectada neste install. Passe o id ou o rótulo (match parcial). Omita se só há uma. Use kb_list_accounts para descobrir. |

#### `kb_get_document`

Metadados + status de um documento específico (sem o texto cru). _(POST /api/kb/get/document)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `document_id` | string | Sim | ID do documento (campo `_id` de kb_list_documents). |
| `account` | string | Não | Seletor opcional da base de conhecimento quando há mais de uma conectada neste install. Passe o id ou o rótulo (match parcial). Omita se só há uma. Use kb_list_accounts para descobrir. |
| `document_ids` | string[] | Não | Bulk mode: multiple values for document_id |

#### `kb_ingest_url`

Baixa um arquivo de uma URL (.md/.txt/.docx) e o indexa na base. _(POST /api/kb/ingest/url)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `url` | string | Sim | URL do arquivo a ingerir. |
| `filename` | string | Não | Nome do arquivo (opcional; inferido da URL se omitido). |
| `account` | string | Não | Seletor opcional da base de conhecimento quando há mais de uma conectada neste install. Passe o id ou o rótulo (match parcial). Omita se só há uma. Use kb_list_accounts para descobrir. |

#### `kb_list_accounts`

Lista as bases de conhecimento conectadas neste install. _(POST /api/kb/list/accounts)_

#### `kb_list_documents`

Lista os documentos da base (id, nome, status, tamanho, nº de chunks). _(POST /api/kb/list/documents)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Seletor opcional da base de conhecimento quando há mais de uma conectada neste install. Passe o id ou o rótulo (match parcial). Omita se só há uma. Use kb_list_accounts para descobrir. |

#### `kb_remove_document`

Remove um ou mais documentos da base (apaga o original, os chunks e o índice). _(POST /api/kb/remove/document)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `document_ids` | string[] | Sim | IDs dos documentos a remover (de kb_list_documents). |
| `account` | string | Não | Seletor opcional da base de conhecimento quando há mais de uma conectada neste install. Passe o id ou o rótulo (match parcial). Omita se só há uma. Use kb_list_accounts para descobrir. |

#### `kb_search`

Busca semântica na base de conhecimento. _(POST /api/kb/search)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `query` | string | Sim | A pergunta/consulta em linguagem natural. |
| `top_k` | integer | Não | Quantos trechos retornar (default 5). |
| `account` | string | Não | Seletor opcional da base de conhecimento quando há mais de uma conectada neste install. Passe o id ou o rótulo (match parcial). Omita se só há uma. Use kb_list_accounts para descobrir. |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_kb` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
