---
reusableId: 178
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

## **Data Communication Sequence**

Viewtisight REST API is in charge of accessing metadata, database and configuration parameters stored in Viewticore Layer, where all complexity resides. Thus, it is possible to retrieve all necessary data without having into account all the configuration performed in databases and so on.

Although this data retrieval is fully described in the API INTEGRATION section, here is an example about how communication works when using Viewtisight API REST:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/OTB61qMx8Kn7tZP5CVIU.png" align="center"></figure>

<br />

---

## **API Specification**

<br />

## **Auth**

### GET /auth/\*

Get from Viewtiauth API. (`authControllerGet`) **Responses:**

-   `200`: The record has been successfully queried.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

### POST /auth/\*

Post to Viewtiauth API. (`authControllerPut`) **Responses:**

-   `200`: The record has been successfully queried/created.
-   `400`: Bad Request.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

<br />

## **Dashboards**

### POST /dashboards/wall

Update an application instance of the model and persist it into the data source. (`dashboardsControllerCreatewall`) **Consumes:** `application/json` **Request body:** `body DashboardWallDto` (required) **Responses:**

-   `201`: The record has been successfully created.
-   `400`: Unprocessable Entity.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `422`: Entity Validation Error.

<br />

### GET /dashboards

Find all instances of the model matched by filter from the data source. (`dashboardsControllerFindAll`) **Responses:**

-   `200`: The records has been successfully queried.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

<br />

### GET /dashboards/{name}

Find a model instance by `name` from the data source. (`dashboardsControllerFindOne`) **Path parameters:** `name` (required) **Responses:**

-   `200`: The record has been successfully queried.
-   `400`: Bad Request.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

<br />

### DELETE /dashboards/{app}/{id}

Delete a model instance by `id` from `app` in the data source. (`dashboardsControllerRemove`) **Path parameters:** `app` (required), `id` (required) **Responses:**

-   `200`: The record has been successfully deleted.
-   `400`: Bad Request.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

<br />

### PUT /dashboards/{app}

Update an application instance of the model and persist it into the data source. (`dashboardsControllerUpdate`) **Path parameters:** `app` (required) **Consumes:** `application/json` **Request body:** `body UpdateDashboardDto` (required) **Responses:**

-   `201`: The record has been successfully created.
-   `400`: Unprocessable Entity.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `422`: Entity Validation Error.

<br />

### PUT /dashboards/wall/{menu}/{name}

Update an application instance of the model and persist it into the data source. (`dashboardsControllerUpdateWallName`) **Path parameters:** `menu` (required), `name` (required) **Responses:**

-   `201`: The record has been successfully created.
-   `400`: Unprocessable Entity.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `422`: Entity Validation Error.

<br />

## **Data**

### POST /data/{set}/query

Find a model instance by `set` from the data source. (`dataControllerGetData`) **Path parameters:** `set` (required) **Consumes:** `application/json` **Request body:** `body DataDto` (required) **Responses:**

-   `200`: The record has been successfully queried.
-   `400`: Bad Request.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

<br />

### GET /data/{set}/fields

Find a model instance by `set` from the data source. (`dataControllerGetFields`) **Path parameters:** `set` (required) **Responses:**

-   `200`: The record has been successfully queried.
-   `400`: Bad Request.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

### GET /data/sets

Find all instances of the model matched by filter from the data source. (`dataControllerGetSets`) **Responses:**

-   `200`: The records has been successfully queried.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

<br />

## **Default**

### GET /queryobjects

Find all instances of the model matched by filter from the data source. (`queryobjectsControllerFindAll`) **Responses:**

-   `200`: The records has been successfully queried.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

### GET /queryobjects/{set}

Find a model instance by `set` from the data source. (`queryobjectsControllerFindOne`) **Path parameters:** `set` (required) **Responses:**

-   `200`: The record has been successfully queried.
-   `400`: Bad Request.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

## **Menus**

### DELETE /menus/{menuId}

Modify user preferences based on `userId` (`menusControllerDelete`) **Path parameters:** `menuId` (required) **Responses:**

-   `201`: The record has been successfully created.
-   `400`: Unprocessable Entity.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `422`: Entity Validation Error.

### GET /menus

Find all instances of the model matched by filter from the data source. (`menusControllerFindAll`) **Responses:**

-   `200`: The records has been successfully queried.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

### PUT /menus/{menuId}

Modify user preferences based on `userId` (`menusControllerUpdate`) **Path parameters:** `menuId` (required) **Consumes:** `application/json` **Request body:** `body MenuDto` (required) **Responses:**

-   `201`: The record has been successfully created.
-   `400`: Unprocessable Entity.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `422`: Entity Validation Error.

## Pcap

### POST /pcap

Execute gRPC method to generate Pcap File. (`pcapControllerCall`) **Consumes:** `application/json` **Request body:** `body PcapDto` (required) **Responses:**

-   `200`: File was generated correctly.
-   `500`: Internal Server Error.

### GET /pcap/getFile/{id}

Execute gRPC method to generate Pcap File. (`pcapControllerGetFile`) **Path parameters:** `id` (required) **Responses:**

-   `200`: File was generated correctly.
-   `500`: Internal Server Error.

## Preferences

### POST /preferences

Create a new instance of the model and persist it into the data source. (`preferencesControllerCreate`) **Consumes:** `application/json` **Request body:** `body CreatePreferenceDto` (required) **Responses:**

-   `201`: The record has been successfully created.
-   `400`: Unprocessable Entity.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `422`: Entity Validation Error.

### GET /preferences

Find all instances of the model matched by filter from the data source. (`preferencesControllerFindAll`) **Responses:**

-   `200`: The records has been successfully queried.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

### GET /preferences/{id}

Find a model instance by `id` from the data source. (`preferencesControllerFindOne`) **Path parameters:** `id` (required) **Responses:**

-   `200`: The record has been successfully queried.
-   `400`: Bad Request.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

### GET /preferences/getPrefByUserId/{userId}

Find a model instance by `userId` from the data source. (`preferencesControllerGetPrefByUserId`) **Path parameters:** `userId` (required) **Responses:**

-   `200`: The record has been successfully queried.
-   `400`: Bad Request.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `404`: Not Found.

### PUT /preferences/{userId}

Modify user preferences based on `userId` (`preferencesControllerUpdate`) **Path parameters:** `userId` (required) **Consumes:** `application/json` **Request body:** `body UpdatePreferenceDto` (required) **Responses:**

-   `201`: The record has been successfully created.
-   `400`: Unprocessable Entity.
-   `401`: Unauthorized.
-   `403`: Forbidden.
-   `422`: Entity Validation Error.

## Models

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

## **Data Model**

Understanding how information is combined in the data model is crucial in order to perform integrations with Viewtisght REST API.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/5eTVFAdVA5YE8owBnid9.png"></figure>

<br />

-   **Reports** are stored in its own collection. These objects can be embedded in queries in order to get the desired KQIs.
-   **Metadata** is needed in order to know which sets (e.g., tables) can be queried and which fields are available for each set.

Once these two data sources are combined, a correct query can be generated in order to retrieve data from Data Layer.

In case dashboards have been provided or created by Viewtisight GUI, there is an additional datasource named **Dashboards** that is a set of several KQIs combined together to provide meaningful statistics. These are useful to perform a predefined set of queries.