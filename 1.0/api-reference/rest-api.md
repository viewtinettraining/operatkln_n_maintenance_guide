---
reusableId: 178
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'API REST'
id: C1C-3ZC-317-MUQ
slug: rest-api
isVisible: true
isSearchable: true
lastUpdated: '2026-06-02 08:54:27'
---
# **<span align="center">API REST</span>**

<br />

## **Sequência de Comunicação de Dados**

A API REST do Viewtisight é responsável por acessar metadados, banco de dados e parâmetros de configuração armazenados na Camada Viewticore, onde toda a complexidade reside. Assim, é possível recuperar todos os dados necessários sem precisar considerar toda a configuração realizada nos bancos de dados, etc.

Embora essa recuperação de dados seja totalmente descrita na seção de INTEGRAÇÃO DA API, aqui está um exemplo de como a comunicação funciona ao usar a API REST do Viewtisight:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/OTB61qMx8Kn7tZP5CVIU.png" align="center"></figure>

<br />

---

## **Especificação da API**

<br />

## **Autenticação**

### GET /auth/\*

Obtém dados da API Viewtiauth. (`authControllerGet`) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### POST /auth/\*

Envia dados para a API Viewtiauth. (`authControllerPut`) **Respostas:**

-   `200`: O registro foi consultado/criado com sucesso.
-   `400`: Requisição inválida.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

## **Dashboards**

### POST /dashboards/wall

Atualiza uma instância do modelo e persiste na fonte de dados. (`dashboardsControllerCreatewall`) **Consome:** `application/json` **Corpo da requisição:** `body DashboardWallDto` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

<br />

### GET /dashboards

Encontra todas as instâncias do modelo correspondentes ao filtro na fonte de dados. (`dashboardsControllerFindAll`) **Respostas:**

-   `200`: Os registros foram consultados com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

### GET /dashboards/{name}

Encontra uma instância do modelo pelo `name` na fonte de dados. (`dashboardsControllerFindOne`) **Parâmetros de caminho:** `name` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição inválida.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

### DELETE /dashboards/{app}/{id}

Exclui uma instância do modelo pelo `id` de `app` na fonte de dados. (`dashboardsControllerRemove`) **Parâmetros de caminho:** `app` (obrigatório), `id` (obrigatório) **Respostas:**

-   `200`: O registro foi excluído com sucesso.
-   `400`: Requisição inválida.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

### PUT /dashboards/{app}

Atualiza uma instância do modelo e persiste na fonte de dados. (`dashboardsControllerUpdate`) **Parâmetros de caminho:** `app` (obrigatório) **Consome:** `application/json` **Corpo da requisição:** `body UpdateDashboardDto` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

<br />

### PUT /dashboards/wall/{menu}/{name}

Atualiza uma instância do modelo e persiste na fonte de dados. (`dashboardsControllerUpdateWallName`) **Parâmetros de caminho:** `menu` (obrigatório), `name` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

<br />

## **Dados**

### POST /data/{set}/query

Encontra uma instância do modelo pelo `set` na fonte de dados. (`dataControllerGetData`) **Parâmetros de caminho:** `set` (obrigatório) **Consome:** `application/json` **Corpo da requisição:** `body DataDto` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição inválida.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

### GET /data/{set}/fields

Encontra uma instância do modelo pelo `set` na fonte de dados. (`dataControllerGetFields`) **Parâmetros de caminho:** `set` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição inválida.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### GET /data/sets

Encontra todas as instâncias do modelo correspondentes ao filtro na fonte de dados. (`dataControllerGetSets`) **Respostas:**

-   `200`: Os registros foram consultados com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

## **Padrão**

### GET /queryobjects

Encontra todas as instâncias do modelo correspondentes ao filtro na fonte de dados. (`queryobjectsControllerFindAll`) **Respostas:**

-   `200`: Os registros foram consultados com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### GET /queryobjects/{set}

Encontra uma instância do modelo pelo `set` na fonte de dados. (`queryobjectsControllerFindOne`) **Parâmetros de caminho:** `set` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição inválida.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

## **Menus**

### DELETE /menus/{menuId}

Modifica as preferências do usuário com base no `userId` (`menusControllerDelete`) **Parâmetros de caminho:** `menuId` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

### GET /menus

Encontra todas as instâncias do modelo correspondentes ao filtro na fonte de dados. (`menusControllerFindAll`) **Respostas:**

-   `200`: Os registros foram consultados com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### PUT /menus/{menuId}

Modifica as preferências do usuário com base no `userId` (`menusControllerUpdate`) **Parâmetros de caminho:** `menuId` (obrigatório) **Consome:** `application/json` **Corpo da requisição:** `body MenuDto` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

## Pcap

### POST /pcap

Executa o método gRPC para gerar arquivo Pcap. (`pcapControllerCall`) **Consome:** `application/json` **Corpo da requisição:** `body PcapDto` (obrigatório) **Respostas:**

-   `200`: Arquivo gerado corretamente.
-   `500`: Erro interno do servidor.

### GET /pcap/getFile/{id}

Executa o método gRPC para gerar arquivo Pcap. (`pcapControllerGetFile`) **Parâmetros de caminho:** `id` (obrigatório) **Respostas:**

-   `200`: Arquivo gerado corretamente.
-   `500`: Erro interno do servidor.

## Preferências

### POST /preferences

Cria uma nova instância do modelo e persiste na fonte de dados. (`preferencesControllerCreate`) **Consome:** `application/json` **Corpo da requisição:** `body CreatePreferenceDto` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

### GET /preferences

Encontra todas as instâncias do modelo correspondentes ao filtro na fonte de dados. (`preferencesControllerFindAll`) **Respostas:**

-   `200`: Os registros foram consultados com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### GET /preferences/{id}

Encontra uma instância do modelo pelo `id` na fonte de dados. (`preferencesControllerFindOne`) **Parâmetros de caminho:** `id` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição inválida.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### GET /preferences/getPrefByUserId/{userId}

Encontra uma instância do modelo pelo `userId` na fonte de dados. (`preferencesControllerGetPrefByUserId`) **Parâmetros de caminho:** `userId` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição inválida.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### PUT /preferences/{userId}

Modifica as preferências do usuário com base no `userId` (`preferencesControllerUpdate`) **Parâmetros de caminho:** `userId` (obrigatório) **Consome:** `application/json` **Corpo da requisição:** `body UpdatePreferenceDto` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

## Modelos

### 1\. CreatePreferenceDto

-   `userId` (String)
-   `guiData` (Object)

### 2\. DashboardWallDto

-   `name` (String)
-   `config` (array\[String\])
-   `created_at` (BigDecimal)
-   `updated_at` (BigDecimal)
-   `active` (Boolean)

### 3\. DataDto

-   `size` (Boolean)
-   `fields` (Object)
-   `group` (Object)
-   `order` (Object)
-   `timerange` (Object)
-   `limit` (Object)
-   `granularity` (Object)

### 4\. MenuDto

-   `name` (String)
-   `editable` (Boolean)
-   `icon` (String)
-   `title` (String)
-   `link` (String)
-   `submenu` (array\[String\])
-   `active` (Boolean)

### 5\. PcapDto

-   `from` (BigDecimal)
-   `to` (BigDecimal)
-   `tuples` (array\[String\])
-   `ranges` (array\[String\])

### 6\. UpdateDashboardDto

-   `_id` (BigDecimal)
-   `title` (String)
-   `descripIntl` (array\[String\])
-   `logo` (String)
-   `lastCardId` (BigDecimal)
-   `numCards` (BigDecimal)
-   `cards` (array\[String\])
-   `created_at` (BigDecimal)
-   `updated_at` (BigDecimal)
-   `active` (Boolean)

### 7\. UpdatePreferenceDto

-   `guiData` (Object)

---

## **Modelo de Dados**

Entender como as informações são combinadas no modelo de dados é fundamental para realizar integrações com a API REST do Viewtisight.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/5eTVFAdVA5YE8owBnid9.png"></figure>

<br />

-   **Relatórios** são armazenados em sua própria coleção. Esses objetos podem ser incorporados em consultas para obter os KQIs desejados.
-   **Metadados** são necessários para saber quais conjuntos (ex.: tabelas) podem ser consultados e quais campos estão disponíveis para cada conjunto.

Uma vez combinadas essas duas fontes de dados, uma consulta correta pode ser gerada para recuperar dados da Camada de Dados.

Caso dashboards tenham sido fornecidos ou criados pela interface gráfica do Viewtisight, existe uma fonte de dados adicional chamada **Dashboards**, que é um conjunto de vários KQIs combinados para fornecer estatísticas significativas. Esses são úteis para executar um conjunto predefinido de consultas.
