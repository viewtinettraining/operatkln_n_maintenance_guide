---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Integração via API REST'
id: R4L-IQM-VCO-LYU
slug: rest-api-integration
isVisible: true
isSearchable: true
lastUpdated: '2026-06-02 08:54:45'
---
# **<span align="center">INTEGRAÇÃO DE API REST</span>**

<br />

## **Autenticação**

A autenticação é necessária para realizar qualquer chamada à API REST do Viewtisight. Essa autenticação é baseada em OAuth 2.0 e segue a mesma sequência:

<br />

Aqui está um exemplo de como obter o token de autenticação para realizar qualquer chamada usando o comando `curl`:

```bash
curl -X POST "http://192.168.1.199:4000/auth/login" -H "accept: application/json" -H "Content-Type: application/json" -d '{ "username": "admin", "password": "viewtinet", "clear_pass" : true}'
```

**Exemplo de Resposta:**

```json
{"_id":"5db9a9b7973fac39d8d48512","username":"devel","email":"devel@viewtinet.com","name":"Developer","lastname":"","access_token":"eyJhbG...","expiresIn":3600000}
```

Note que o mesmo endpoint pode ser acessado via https na porta 4001:<br />
`https://192.168.1.187:4001/auth/login`

Se a autenticação for bem-sucedida, o `access_token` deve ser armazenado e usado nas chamadas de API seguintes para aceitar requisições GET e POST. Da mesma forma, a cifra pode ser usada como parâmetro de url auth ao acessar o frontend, conforme explicado no capítulo de Integração do Viewtisight.

<br />

## **Requisições de Conjuntos (Sets)**

A sequência para solicitar conjuntos é a seguinte:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img4.png" align="center"></figure>

<br />

Este é um exemplo de como obter conjuntos usando o comando `curl`:

```bash
curl -X GET "http://192.168.1.199:4101/data/sets" -H "accept: /" -H "authorization: bearer eyJhb..."
```

**Exemplo de Resposta:**

```json
{"idrequest":"a2976ca1-8846-47bb-bd21-3cde4cb8e877","sets":["dpi_records","pcap_storage_records"]}
```

No exemplo anterior, haveria dois conjuntos: `dpi_records` e `pcap_storage_records` que podem ser consultados.

<br />

## **Requisições de campos de conjuntos**

A sequência para solicitar campos para um determinado conjunto é a seguinte:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img5.png" align="center"></figure>

<br />

Os campos conterão os seguintes atributos:

-   `type` → Tipo de Objeto: `STRING`, `ULONG`, `LONG`, `IPADDRESSV6`, `IPADDRESSV4`, `UINT`, `INT`, `DOUBLE`
-   `name` → nome do campo

Este é um exemplo de como obter campos de conjunto usando o comando `curl`:

```bash
curl -X GET "http://192.168.1.171:4101/data/dpi_records/fields" -H "accept: /" -H "authorization: bearer eyJhb..."
```

**Exemplo de Resposta:**

```json
{"err":"Success","idrequest":"...","set":"dpi_records","fields":[{"type":"STRING","name":"app_name"},{"type":"ULONG","name":"connection_time"},...]}
```

No exemplo anterior, esta seria a lista de campos e metadados para o conjunto `dpi_records`. Ter a lista de campos permite que integrações externas criem requisições de dados no formato de consulta adequado.

<br />

## Requisições de Relatórios/KQIs

A sequência para solicitar relatórios é a seguinte:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img6.png" align="center"></figure>

<br />

Esta chamada retornará a lista de todos os relatórios disponíveis no sistema. Aqui está um exemplo usando o comando `curl`:

```bash
curl -X GET "http://192.168.1.171:4101/queryobjects" -H "accept: /" -H "authorization: bearer eyJhb..."
```

Se forem necessários apenas relatórios de um conjunto específico, existe outra chamada:<br />
`http://&lt;VIEWTISIGIHT_AP_ADDRESS&gt;/queryobjects/&lt;set&gt;`

Aqui está um exemplo usando o comando `curl`:

```bash
curl -X GET "http://192.168.1.171:4101/queryobjects/dpi_records" -H "accept: /" -H "authorization: bearer eyJhb..."
```

<br />

## **Requisições de Dashboards**

A sequência para solicitar dashboards é a seguinte:

Esta chamada retornará a lista de todos os dashboards disponíveis no sistema. Aqui está um exemplo usando o comando `curl`:

```bash
curl -X GET "http://192.168.1.171:4101/dashboards" -H "accept: /" -H "authorization: bearer eyJhb..."
```

Os dashboards são úteis porque possuem consultas predefinidas com algum significado (por exemplo, Dashboard de desempenho de rede) e permitem que integrações executem consultas apenas pegando a resposta do dashboard. Se os dashboards não estiverem definidos, o usuário terá que combinar metadados do conjunto e relatórios do conjunto para recuperar dados.

<br />

## **Requisições de dados**

O Viewtisight armazena informações tanto em registros brutos (geralmente milhões de registros) quanto em agregados, a fim de acelerar as consultas. No entanto, apenas as tabelas brutas são mostradas e as tabelas agregadas são internas, pois são usadas automaticamente pelo sistema dependendo da consulta recebida. Ou seja, há um agendador de consultas avaliando qual tabela é a melhor que pode retornar os resultados da maneira mais rápida e completa, sendo este processo transparente para os usuários.

Estes são os parâmetros para realizar a requisição de dados, usando o formato de consulta:

-   `fields`
    
    -   `list`: lista de campos a serem recuperados com qualquer operação de agregação. Eles são usados para obter todos os registros das tabelas sem nenhum tipo de agrupamento ou agregação.
-   `filters`: lista de filtros para executar sobre as colunas nas tabelas (por exemplo, filtrar por um endereço IP específico).
-   `group`
    
    -   `list`: lista de campos a serem recuperados aplicando operações de agregação e agrupamento. Existem 3 tipos de campos na lista de grupos:
    -   `dimension`: colunas de string que serão usadas para agrupar relatórios (por exemplo, endereço ip de origem).
    -   `metric`: coluna numérica que aplicará alguma operação de agregação (por exemplo, SUM).
    -   `calculated`: combinação de campos de métrica ou valores constantes para realizar operações matemáticas avançadas.
-   `filters`: lista de filtros para executar sobre registros já agregados (por exemplo, filtrar registros com uma SUM(coluna) maior que 1000).
-   `order`
    
    -   `list`: lista de campos de ordem para realizar a operação de ordenação. A ordem crescente e decrescente é suportada para qualquer tipo de coluna.
-   `limit`: Operação para limitar os resultados. Útil para obter os elementos superiores/inferiores ou iterar sobre uma tabela paginada.
-   `offset`: deslocamento para começar a retornar os registros.
-   `count`: número de registros a retornar.
-   `timerange`: intervalos de tempo para a consulta.
    
    -   `start`: carimbo de data/hora usado para iniciar a pesquisa.
    -   `end`: carimbo de data/hora usado para finalizar a pesquisa.
    -   `timefield`: campo usado para realizar a pesquisa temporal.
-   `size`: valor true/false (verdadeiro/falso). Se for verdadeiro, o número de registros retornados pela consulta estará disponível na resposta.
-   `granularity`: usado para receber registros no formato de série temporal.
    
    -   `value`: valor do intervalo de tempo (bucket).
    -   `unit`: unidade na qual o valor é definido. Estes são os valores disponíveis:
    -   segundo
    -   minuto
    -   hora
    -   semana
    -   dia
    -   ano

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img7.png" align="center"></figure>

<br />

### **Exemplos**

Aqui estão alguns exemplos de consultas realizadas usando o conjunto `dpi_records`, que contém estatísticas extraídas pelo Viewtimon DPI:

#### Volume Total (Rede)

```bash
curl 'http://192.168.1.200:4101/data/dpi_records/query' \
  -H 'Authorization: bearer eyJhb...' \
  -H 'Content-Type: application/json' \
  --data-raw '[{"type":"main","vals":{"size":false,"fields":{},"group":{"list":[{"calculated":{"name":"total_bytes","operation":"add","fields":[{"metric":{"name":"volume_downlink","operation":"sum"}},{"metric":{"name":"volume_uplink","operation":"sum"}}]}}]},"limit":{"seriesFilter":10},"granularity":{"value":"1","unit":"minute"},"subqueries":[],"subQueriesOperator":"","alias":"","timerange":{"start":"1697013960000000","end":"1697017559999999","timefield":"timestamp"},"order":{"list":[{"name":"timestamp","order":"asc"},{"name":"total_bytes","order":"desc"}]},"allowDimensions":true,"isTimeSeries":true}}]' \
  --compressed
```

#### Volume Total por aplicativo

```bash
curl 'http://192.168.1.200:4101/data/dpi_records/query' \
  -H 'Authorization: bearer eyJhb...' \
  -H 'Content-Type: application/json' \
  --data-raw '[{"type":"main","vals":{"size":false,"fields":{},"group":{"list":[{"dimension":{"name":"app_name","alias":"app_name"}},{"calculated":{"name":"total_bytes","operation":"add","fields":[{"metric":{"name":"volume_downlink","operation":"sum"}},{"metric":{"name":"volume_uplink","operation":"sum"}}]}}]},"limit":{"count":10,"seriesFilter":10},"granularity":{"value":1,"unit":"minute"},"subqueries":[],"subQueriesOperator":"","alias":"","timerange":{"start":"1697013960000000","end":"1697017559999999","timefield":"timestamp"},"order":{"list":[{"name":"total_bytes","order":"desc"},{"name":"app_name","order":"asc"}]},"allowDimensions":true,"isTimeSeries":false}}]' \
  --compressed
```

#### Volume Total pelo aplicativo "youtube"

```bash
curl 'http://192.168.1.200:4101/data/dpi_records/query' \
  -H 'Authorization: bearer eyJhb...' \
  -H 'Content-Type: application/json' \
  --data-raw '[{"type":"main","vals":{"size":false,"fields":{"filter":{"logical":{"operator":"and","expressions":[{"comparison":{"name":"app_name","fieldType":"string","operator":"eq","value":"\'youtube\'"}}]}}},"group":{"list":[{"dimension":{"name":"app_name","alias":"app_name","cast":""}},{"calculated":{"name":"total_bytes","operation":"add","fields":[{"metric":{"name":"volume_downlink","operation":"sum"}},{"metric":{"name":"volume_uplink","operation":"sum"}}]}}]},"limit":{"count":10,"seriesFilter":10},"granularity":{"value":5,"unit":"minute"},"subqueries":[],"subQueriesOperator":"","alias":"","timerange":{"start":"1697014200000000","end":"1697017799999999","timefield":"timestamp"},"order":{"list":[{"name":"total_bytes","order":"desc"},{"name":"app_name","order":"asc"}]},"allowDimensions":true,"isTimeSeries":false}}]' \
  --compressed
```

<br />

## **Sair (Logout)**

O processo de logout invalida o token da sessão atual.

Este é um exemplo de como realizar um logout usando o comando `curl`:

```bash
curl -X POST "http://<VIEWTISIGHT_IP>:4000/auth/logout" \
  -H "Accept: /" \
  -H "Content-Type: application/json" \
  -H "Authorization: bearer <TOKEN>"
```

<br />

## **Exemplo de Integração com Python**

A seguir está um exemplo de script Python completo baseado nos métodos explicados neste guia. Este script demonstra como autenticar, recuperar dados (neste exemplo, buscando os conjuntos disponíveis), salvar a resposta e, por fim, sair de forma segura.

```python
import requests
from requests.exceptions import HTTPError, Timeout, ConnectionError, RequestException
import json

# Authentication URL
# MODIFY TO MATCH YOUR VIEWTISIGHT IP
url = "http://192.168.50.14:4000/auth/login"

# Dynamically obtain the Viewtinet IP from the URL
viewtinet_ip = url.split("//")[1].split(":")[0]

# Required headers
headers = {
    "Accept": "application/json",
    "Content-Type": "application/json"
}

# Viewtinet user credentials (unique for each installation)
# MODIFY TO MATCH YOUR CREDENTIALS
data = {
    "username": "api_viewtinet",
    "password": "2024Viewtinet!",
    "clear_pass": True
}

def get_credentials(url, headers, data):
    """
    Function to obtain the API token from Viewtinet.
    """
    try:
        # POST Request
        response = requests.post(url, headers=headers, json=data, timeout=10)

        # Check if HTTP response is successful (2xx)
        response.raise_for_status()

        # Convert response to JSON and extract token
        json_response = response.json()
        token = json_response["access_token"]

    except HTTPError as http_err:
        print(f"HTTP error occurred: {http_err}")
    except Timeout as timeout_err:
        print(f"Timeout error: {timeout_err}")
    except ConnectionError as conn_err:
        print(f"Error connecting: {conn_err}")
    except RequestException as req_err:
        print(f"An error occurred: {req_err}")
    except ValueError:
        print("Error decoding JSON response.")
    except KeyError:
        print("Token not found in response.")
    else:
        print("Authentication successful.")
        return token
    return None

def get_data_sets(token):
    """
    Function to dynamically obtain the available sets.
    """
    url = f"http://{viewtinet_ip}:4101/data/sets"

    headers = {
        "Accept": "/",
        "Content-Type": "application/json",
        "Authorization": f"bearer {token}"
    }

    try:
        response = requests.get(url, headers=headers, verify=False, timeout=10)
        response.raise_for_status()

        data = response.json()

        with open("sets_response.json", "w", encoding="utf-8") as f:
            json.dump(data, f, indent=4, ensure_ascii=False)
        print("Response saved successfully in 'sets_response.json'.")

    except Exception as e:
        print(f"An error occurred while fetching sets: {e}")

def logout(token):
    """
    Function to invalidate the current session token.
    """
    url = f"http://{viewtinet_ip}:4000/auth/logout"

    headers = {
        "Accept": "/",
        "Content-Type": "application/json",
        "Authorization": f"bearer {token}"
    }

    try:
        response = requests.post(url, headers=headers, verify=False, timeout=10)
        response.raise_for_status()

        print("Logout successful.")
    except Exception as e:
        print(f"An error occurred during logout: {e}")

def main():
    # 1. Obtain the token
    token = get_credentials(url, headers, data)

    if token:
        # 2. Perform API requests (e.g., getting sets)
        get_data_sets(token)

        # 3. Securely logout
        logout(token)

# Execute the main script
main()
```

<br />