---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Rest api'
id: C1C-3ZC-317-MUQ
slug: rest-api
isVisible: true
isSearchable: true
lastUpdated: '2026-06-02 08:54:27'
---
# **<span align="center">REST API</span>**

<br />

## **Sequência de Comunicação de Dados**

A API REST do Viewtisight é responsável por acessar metadados, banco de dados e parâmetros de configuração armazenados na Camada Viewticore, onde reside toda a complexidade. Assim, é possível recuperar todos os dados necessários sem levar em conta toda a configuração realizada em bancos de dados e afins.

Embora essa recuperação de dados seja descrita detalhadamente na seção de INTEGRAÇÃO DE API, aqui está um exemplo de como a comunicação funciona ao usar a API REST do Viewtisight:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/OTB61qMx8Kn7tZP5CVIU.png" align="center"></figure>

<br />

---

## **Especificação da API**

<br />

## **Autenticação (Auth)**

### GET /auth/\*

Obter da API do Viewtiauth. (`authControllerGet`) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### POST /auth/\*

Postar na API do Viewtiauth. (`authControllerPut`) **Respostas:**

-   `200`: O registro foi consultado/criado com sucesso.
-   `400`: Requisição ruim (Bad Request).
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

## **Dashboards**

### POST /dashboards/wall

Atualizar uma instância de aplicativo do modelo e persisti-la na fonte de dados. (`dashboardsControllerCreatewall`) **Consome:** `application/json` **Corpo da requisição:** `body DashboardWallDto` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

<br />

### GET /dashboards

Encontrar todas as instâncias do modelo correspondentes ao filtro da fonte de dados. (`dashboardsControllerFindAll`) **Respostas:**

-   `200`: Os registros foram consultados com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

### GET /dashboards/{name}

Encontrar uma instância de modelo por `name` da fonte de dados. (`dashboardsControllerFindOne`) **Parâmetros de caminho:** `name` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição ruim (Bad Request).
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

### DELETE /dashboards/{app}/{id}

Excluir uma instância de modelo por `id` do `app` na fonte de dados. (`dashboardsControllerRemove`) **Parâmetros de caminho:** `app` (obrigatório), `id` (obrigatório) **Respostas:**

-   `200`: O registro foi excluído com sucesso.
-   `400`: Requisição ruim (Bad Request).
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

### PUT /dashboards/{app}

Atualizar uma instância de aplicativo do modelo e persisti-la na fonte de dados. (`dashboardsControllerUpdate`) **Parâmetros de caminho:** `app` (obrigatório) **Consome:** `application/json` **Corpo da requisição:** `body UpdateDashboardDto` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

<br />

### PUT /dashboards/wall/{menu}/{name}

Atualizar uma instância de aplicativo do modelo e persisti-la na fonte de dados. (`dashboardsControllerUpdateWallName`) **Parâmetros de caminho:** `menu` (obrigatório), `name` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

<br />

## **Dados**

### POST /data/{set}/query

Encontrar uma instância de modelo por `set` da fonte de dados. (`dataControllerGetData`) **Parâmetros de caminho:** `set` (obrigatório) **Consome:** `application/json` **Corpo da requisição:** `body DataDto` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição ruim (Bad Request).
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

### GET /data/{set}/fields

Encontrar uma instância de modelo por `set` da fonte de dados. (`dataControllerGetFields`) **Parâmetros de caminho:** `set` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição ruim (Bad Request).
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### GET /data/sets

Encontrar todas as instâncias do modelo correspondentes ao filtro da fonte de dados. (`dataControllerGetSets`) **Respostas:**

-   `200`: Os registros foram consultados com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

<br />

## **Padrão (Default)**

### GET /queryobjects

Encontrar todas as instâncias do modelo correspondentes ao filtro da fonte de dados. (`queryobjectsControllerFindAll`) **Respostas:**

-   `200`: Os registros foram consultados com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### GET /queryobjects/{set}

Encontrar uma instância de modelo por `set` da fonte de dados. (`queryobjectsControllerFindOne`) **Parâmetros de caminho:** `set` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição ruim (Bad Request).
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

## **Menus**

### DELETE /menus/{menuId}

Modificar preferências do usuário com base no `userId` (`menusControllerDelete`) **Parâmetros de caminho:** `menuId` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

### GET /menus

Encontrar todas as instâncias do modelo correspondentes ao filtro da fonte de dados. (`menusControllerFindAll`) **Respostas:**

-   `200`: Os registros foram consultados com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### PUT /menus/{menuId}

Modificar preferências do usuário com base no `userId` (`menusControllerUpdate`) **Parâmetros de caminho:** `menuId` (obrigatório) **Consome:** `application/json` **Corpo da requisição:** `body MenuDto` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

## Pcap

### POST /pcap

Executar método gRPC para gerar arquivo Pcap. (`pcapControllerCall`) **Consome:** `application/json` **Corpo da requisição:** `body PcapDto` (obrigatório) **Respostas:**

-   `200`: O arquivo foi gerado corretamente.
-   `500`: Erro interno do servidor.

### GET /pcap/getFile/{id}

Executar método gRPC para gerar arquivo Pcap. (`pcapControllerGetFile`) **Parâmetros de caminho:** `id` (obrigatório) **Respostas:**

-   `200`: O arquivo foi gerado corretamente.
-   `500`: Erro interno do servidor.

## Preferências

### POST /preferences

Criar uma nova instância do modelo e persisti-la na fonte de dados. (`preferencesControllerCreate`) **Consome:** `application/json` **Corpo da requisição:** `body CreatePreferenceDto` (obrigatório) **Respostas:**

-   `201`: O registro foi criado com sucesso.
-   `400`: Entidade não processável.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `422`: Erro de validação de entidade.

### GET /preferences

Encontrar todas as instâncias do modelo correspondentes ao filtro da fonte de dados. (`preferencesControllerFindAll`) **Respostas:**

-   `200`: Os registros foram consultados com sucesso.
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### GET /preferences/{id}

Encontrar uma instância de modelo por `id` da fonte de dados. (`preferencesControllerFindOne`) **Parâmetros de caminho:** `id` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição ruim (Bad Request).
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### GET /preferences/getPrefByUserId/{userId}

Encontrar uma instância de modelo por `userId` da fonte de dados. (`preferencesControllerGetPrefByUserId`) **Parâmetros de caminho:** `userId` (obrigatório) **Respostas:**

-   `200`: O registro foi consultado com sucesso.
-   `400`: Requisição ruim (Bad Request).
-   `401`: Não autorizado.
-   `403`: Proibido.
-   `404`: Não encontrado.

### PUT /preferences/{userId}

Modificar preferências do usuário com base no `userId` (`preferencesControllerUpdate`) **Parâmetros de caminho:** `userId` (obrigatório) **Consome:** `application/json` **Corpo da requisição:** `body UpdatePreferenceDto` (obrigatório) **Respostas:**

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

Entender como a informação é combinada no modelo de dados é crucial a fim de realizar integrações com a API REST do Viewtisight.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/5eTVFAdVA5YE8owBnid9.png"></figure>

<br />

-   **Relatórios** (Reports) são armazenados em sua própria coleção. Estes objetos podem ser embutidos em consultas a fim de obter os KQIs desejados.
-   **Metadados** (Metadata) são necessários para saber quais conjuntos (por exemplo, tabelas) podem ser consultados e quais campos estão disponíveis para cada conjunto.

Uma vez que essas duas fontes de dados são combinadas, uma consulta correta pode ser gerada a fim de recuperar dados da Camada de Dados.

Caso os dashboards tenham sido fornecidos ou criados pela interface gráfica (GUI) do Viewtisight, há uma fonte de dados adicional chamada **Dashboards** que é um conjunto de vários KQIs combinados juntos para fornecer estatísticas significativas. Estes são úteis para realizar um conjunto predefinido de consultas.