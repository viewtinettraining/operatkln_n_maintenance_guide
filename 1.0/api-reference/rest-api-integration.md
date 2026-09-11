---
reusableId: 179
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Integração da API REST'
id: R4L-IQM-VCO-LYU
slug: rest-api-integration
isVisible: true
isSearchable: true
lastUpdated: '2026-06-02 08:54:45'
---
# **<span align="center">INTEGRAÇÃO DA API REST</span>**

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

Observe que o mesmo endpoint pode ser acessado via https na porta 4001:<br />
`https://192.168.1.187:4001/auth/login`

Se a autenticação for bem-sucedida, o `access_token` deve ser armazenado e utilizado nas chamadas de API subsequentes para aceitar tanto requisições GET quanto POST. Da mesma forma, o cipher pode ser usado como parâmetro de URL de autenticidade ao acessar o frontend, conforme explicado no capítulo Integração do Viewtisight.

<br />

## **Requisições de Conjuntos**

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

## **Requisições de Campos do Conjunto**

A sequência para solicitar campos de um determinado conjunto é a seguinte:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img5.png" align="center"></figure>

<br />

Os campos conterão os seguintes atributos:

-   `type` → Tipo do Objeto: `STRING`, `ULONG`, `LONG`, `IPADDRESSV6`, `IPADDRESSV4`, `UINT`, `INT`, `DOUBLE`
-   `name` → nome do campo

Este é um exemplo de como obter campos de conjuntos usando o comando `curl`:

```bash
curl -X GET "http://192.168.1.171:4101/data/dpi_records/fields" -H "accept: /" -H "authorization: bearer eyJhb..."
```

**Exemplo de Resposta:**

```json
{"err":"Success","idrequest":"...","set":"dpi_records","fields":[{"type":"STRING","name":"app_name"},{"type":"ULONG","name":"connection_time"},...]}
```

No exemplo anterior, esta seria a lista de campos e metadados para o conjunto `dpi_records`. Ter a lista de campos permite que integrações externas criem requisições de dados no formato de consulta correto.

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

Se apenas relatórios de um conjunto específico forem necessários, existe outra chamada:<br />
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

Os dashboards são úteis pois possuem consultas predefinidas com significado (ex.: Dashboard de desempenho de rede) e permitem que as integrações realizem consultas apenas capturando a resposta do dashboard. Se os dashboards não estiverem definidos, o usuário terá que combinar metadados de conjunto e relatórios de conjunto para recuperar os dados.

<br />

## **Requisições de Dados**

O Viewtisight armazena informações tanto em registros brutos (geralmente milhões de registros) quanto em registros agregados para acelerar as consultas. No entanto, apenas tabelas brutas são exibidas e as tabelas agregadas são internas, pois são usadas automaticamente pelo sistema dependendo da consulta recebida. Ou seja, existe um agendador de consultas que avalia qual tabela pode retornar resultados da forma mais rápida e completa, sendo esse processo transparente para os usuários.

Estes são os parâmetros para realizar uma requisição de dados, usando o formato de consulta:

-   `fields`
    
    -   `list`: lista de campos a recuperar com qualquer operação de agregação. São usados para obter todos os registros de tabelas sem nenhum tipo de agrupamento ou agregação.
-   `filters`: lista de filtros a aplicar sobre colunas em tabelas (ex.: filtrar por algum endereço IP específico).
-   `group`
    
    -   `list`: lista de campos a recuperar aplicando operações de agregação e agrupamento. Existem 3 tipos de campos de lista de grupo:
    -   `dimension`: colunas de string que serão usadas para agrupamento de relatórios (ex.: endereço IP de origem).
    -   `metric`: coluna numérica que aplicará alguma operação de agregação (ex.: SUM).
    -   `calculated`: combinação de campos métricos ou valores constantes para realizar operações matemáticas avançadas.
-   `filters`: lista de filtros a aplicar sobre registros já agregados (ex.: filtrar registros com SUM(coluna) maior que 1000).
-   `order`
    
    -   `list`: lista de campos de ordenação para realizar operação de ordenação. Ordenação crescente e decrescente são suportadas para qualquer tipo de coluna.
-   `limit`: Operação para limitar resultados. Útil para obter os primeiros/últimos elementos ou iterar sobre uma tabela paginada.
-   `offset`: deslocamento para iniciar o retorno de registros.
-   `count`: número de registros a retornar.
-   `timerange`: intervalos de tempo para consulta.
    
    -   `start`: timestamp usado para iniciar a busca.
    -   `end`: timestamp usado para finalizar a busca.
    -   `timefield`: campo usado para realizar a busca temporal.
-   `size`: valor verdadeiro/falso. Se verdadeiro, o número de registros retornados pela consulta fica disponível na resposta.
-   `granularity`: usado para receber registros no formato de série temporal.
    
    -   `value`: valor do intervalo de tempo.
    -   `unit`: unidade na qual o valor está definido. Estes são os valores disponíveis:
    -   second
    -   minute
    -   hour
    -   week
    -   day
    -   year

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img7.png" align="center"></figure>

<br />

### **Exemplos**

Aqui estão alguns exemplos de consultas realizadas com o conjunto `dpi_records`, que contém estatísticas extraídas pelo DPI do Viewtimon:

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

#### Volume Total por aplicativo "youtube"

```bash
curl 'http://192.168.1.200:4101/data/dpi_records/query' \
  -H 'Authorization: bearer eyJhb...' \
  -H 'Content-Type: application/json' \
  --data-raw '[{"type":"main","vals":{"size":false,"fields":{"filter":{"logical":{"operator":"and","expressions":[{"comparison":{"name":"app_name","fieldType":"string","operator":"eq","value":"\'youtube\'"}}]}}},"group":{"list":[{"dimension":{"name":"app_name","alias":"app_name","cast":""}},{"calculated":{"name":"total_bytes","operation":"add","fields":[{"metric":{"name":"volume_downlink","operation":"sum"}},{"metric":{"name":"volume_uplink","operation":"sum"}}]}}]},"limit":{"count":10,"seriesFilter":10},"granularity":{"value":5,"unit":"minute"},"subqueries":[],"subQueriesOperator":"","alias":"","timerange":{"start":"1697014200000000","end":"1697017799999999","timefield":"timestamp"},"order":{"list":[{"name":"total_bytes","order":"desc"},{"name":"app_name","order":"asc"}]},"allowDimensions":true,"isTimeSeries":false}}]' \
  --compressed
```

<br />

## **Logout**

O processo de logout invalida o token de sessão atual.

Este é um exemplo de como realizar o logout usando o comando `curl`:

```bash
curl -X POST "http://<VIEWTISIGHT_IP>:4000/auth/logout" \
  -H "Accept: /" \
  -H "Content-Type: application/json" \
  -H "Authorization: bearer <TOKEN>"
```

<br />

## **Exemplo de Integração em Python**

A seguir está um exemplo completo de script Python baseado nos métodos explicados neste guia. Este script demonstra como autenticar, recuperar dados (neste exemplo, buscando os conjuntos disponíveis), salvar a resposta e, por fim, realizar o logout com segurança.

```python
import requests
from requests.exceptions import HTTPError, Timeout, ConnectionError, RequestException
import json

# URL de Autenticação
# MODIFIQUE PARA CORRESPONDER AO IP DO SEU VIEWTISIGHT
url = "http://192.168.50.14:4000/auth/login"

# Obter dinamicamente o IP do Viewtinet a partir da URL
viewtinet_ip = url.split("//")[1].split(":")[0]

# Cabeçalhos obrigatórios
headers = {
    "Accept": "application/json",
    "Content-Type": "application/json"
}

# Credenciais do usuário Viewtinet (exclusivas para cada instalação)
# MODIFIQUE PARA CORRESPONDER ÀS SUAS CREDENCIAIS
data = {
    "username": "api_viewtinet",
    "password": "2024Viewtinet!",
    "clear_pass": True
}

def get_credentials(url, headers, data):
    """
    Função para obter o token da API do Viewtinet.
    """
    try:
        # Requisição POST
        response = requests.post(url, headers=headers, json=data, timeout=10)

        # Verificar se a resposta HTTP foi bem-sucedida (2xx)
        response.raise_for_status()

        # Converter resposta para JSON e extrair token
        json_response = response.json()
        token = json_response["access_token"]

    except HTTPError as http_err:
        print(f"Erro HTTP ocorrido: {http_err}")
    except Timeout as timeout_err:
        print(f"Erro de timeout: {timeout_err}")
    except ConnectionError as conn_err:
        print(f"Erro de conexão: {conn_err}")
    except RequestException as req_err:
        print(f"Um erro ocorreu: {req_err}")
    except ValueError:
        print("Erro ao decodificar resposta JSON.")
    except KeyError:
        print("Token não encontrado na resposta.")
    else:
        print("Autenticação bem-sucedida.")
        return token
    return None

def get_data_sets(token):
    """
    Função para obter dinamicamente os conjuntos disponíveis.
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
        print("Resposta salva com sucesso em 'sets_response.json'.")

    except Exception as e:
        print(f"Um erro ocorreu ao buscar conjuntos: {e}")

def logout(token):
    """
    Função para invalidar o token de sessão atual.
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

        print("Logout realizado com sucesso.")
    except Exception as e:
        print(f"Um erro ocorreu durante o logout: {e}")

def main():
    # 1. Obter o token
    token = get_credentials(url, headers, data)

    if token:
        # 2. Realizar requisições à API (ex.: obter conjuntos)
        get_data_sets(token)

        # 3. Realizar logout com segurança
        logout(token)

# Executar o script principal
main()
```

<br />
