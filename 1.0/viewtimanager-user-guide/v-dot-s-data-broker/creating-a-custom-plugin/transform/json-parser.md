---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Analisador JSON (Parser)'
id: JYR-UF1-IMM-QW3
slug: json-parser
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 10:11:39'
---
# **<span align="center">JSON Parser</span>**

<br />

O handler **JSON Parser** é projetado especificamente para extrair elementos aninhados de strings JSON localizadas dentro de uma coluna da grid. Ele analisa a estrutura JSON, recupera os valores desejados e os salva em colunas completamente novas com o tipo de dado apropriado.

> \[!NOTE\] O handler **não** excluirá ou modificará as colunas de origem originais (as "from columns"); ele criará ou modificará apenas as colunas de destino (as "to columns").

---

## **Parâmetros de Configuração**

Para extrair elementos de uma string JSON, você deve definir as regras de mapeamento na configuração:

-   **JSON field separator**: O caractere usado para separar os níveis aninhados ao especificar o caminho para o elemento (por exemplo, `,` ou `:`).
-   **Columns Section**: Clique em **\+ ADD NEW COLUMN** para definir uma regra de extração.
    
    -   **From-column name**: A coluna de origem na grid que contém a string JSON (por exemplo, `payload` ou `owner`).
    -   **JSON field**: O caminho ou chave exata dentro da estrutura JSON para extrair. Para objetos aninhados, você pode usar o separador definido para detalhar (por exemplo, `type:id` se usar `:` como separador, ou `payload.object.issue` usando a notação padrão de ponto).
    -   **To-column name**: O nome da nova coluna onde o valor extraído será armazenado.
    -   **To-column type**: O tipo de dado para o qual o valor extraído será convertido (por exemplo, `string`, `int`).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/json-parser-step1.png" align="center"></figure>

<br />

---

## **Comportamento Esperado**

O exemplo a seguir descreve o comportamento do handler em um cenário prático usando `:` como o separador de campo JSON.

Dada a seguinte grid inicial:

<table><tbody><tr><th><p>owner (string)</p></th><th><p>permissions (string)</p></th></tr><tr><td><p><code>{"user": "admin","tenant": "Viewtinet"}</code></p></td><td><p><code>{"type": {"id": "42","label": "devel"}}</code></p></td></tr><tr><td><p><code>{"user": "dev","tenant": "Client"}</code></p></td><td><p><code>{"type": {"id": "21","label": "labs"}}</code></p></td></tr></tbody></table>

<br />

Se configurarmos o handler para extrair três campos diferentes:

1.  Extraindo o elemento `user` da coluna `owner` para uma nova coluna de string chamada `owner_user`.
2.  Extraindo o elemento `type` da coluna `permissions` para uma nova coluna de string chamada `permissions_type`.
3.  Extraindo o elemento `id` aninhado dentro de `type` da coluna `permissions` (usando o caminho `type:id`) para uma nova coluna de inteiro chamada `permissions_id`.

A grid resultante seria a seguinte:

<table><tbody><tr><th><p>owner (string)</p></th><th><p>permissions (string)</p></th><th><p>owner_user (string)</p></th><th><p>permissions_type (string)</p></th><th><p>permissions_id (int)</p></th></tr><tr><td><p><code>{"user": "admin","tenant": "Viewtinet"}</code></p></td><td><p><code>{"type": {"id": "42","label": "devel"}}</code></p></td><td><p><code>admin</code></p></td><td><p><code>{"id": "42","label": "devel"}</code></p></td><td><p><code>42</code></p></td></tr><tr><td><p><code>{"user": "dev","tenant": "Client"}</code></p></td><td><p><code>{"type": {"id": "21","label": "labs"}}</code></p></td><td><p><code>dev</code></p></td><td><p><code>{"id": "21","label": "labs"}</code></p></td><td><p><code>21</code></p></td></tr></tbody></table>

<br />

### **Explicação:**

-   A primeira nova coluna, `owner_user`, contém o elemento `user` da coluna `owner`, conforme especificado pelo campo JSON `"user"`.
-   A segunda nova coluna, `permissions_type`, contém todo o objeto aninhado `type`, convertido para uma string, conforme especificado pelo campo JSON `"type"`.
-   A terceira nova coluna, `permissions_id`, contém o elemento aninhado duplo `id`, conforme especificado pelo campo JSON `"type:id"`. Observe a lista de elementos separados por `:` usada para percorrer a hierarquia JSON.

<br />