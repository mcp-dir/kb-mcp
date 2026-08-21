# Ferramentas

Base de Conhecimento expõe 7 ferramentas (todas somente leitura).

### 1. `kb_search`
**Input**: `query`, `top_k` (opcional), `account` (opcional)

Busca semântica na base de conhecimento.

### 2. `kb_list_documents`
**Input**: `account` (opcional)

Lista os documentos da base (id, nome, status, tamanho, nº de chunks).

### 3. `kb_get_document`
**Input**: `document_id`, `account` (opcional), `document_ids` (opcional)

Metadados + status de um documento específico (sem o texto cru).

### 4. `kb_add_text`
**Input**: `title`, `text`, `account` (opcional)

Adiciona um texto colado à base (vira um documento indexado e buscável).

### 5. `kb_ingest_url`
**Input**: `url`, `filename` (opcional), `account` (opcional)

Baixa um arquivo de uma URL (.md/.txt/.docx) e o indexa na base.

### 6. `kb_remove_document`
**Input**: `document_ids`, `account` (opcional)

Remove um ou mais documentos da base (apaga o original, os chunks e o índice).

### 7. `kb_list_accounts`
**Input**: nenhum input

Lista as bases de conhecimento conectadas neste install.

## Prompts de exemplo

```
Busque na minha base: qual o prazo de rescisão do contrato padrão?
Adicione esta anotação à base de conhecimento
Liste os documentos da minha base
```
