---
reusableId: 179
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Rest api integration'
id: R4L-IQM-VCO-LYU
slug: rest-api-integration
isVisible: true
isSearchable: true
lastUpdated: '2026-06-02 08:54:45'
---
# **<span align="center">REST API INTEGRATION</span>**

<br />

## **Authentication**

Authentication is needed to perform any call to Viewtisight REST API. This authentication is based on OAuth 2.0 and follows the same sequence:

<br />

Here there is an example of how to get the authentication token to perform any call using `curl` command:

```bash
curl -X POST "http://192.168.1.199:4000/auth/login" -H "accept: application/json" -H "Content-Type: application/json" -d '{ "username": "admin", "password": "viewtinet", "clear_pass" : true}'
```

**Response Example:**

```json
{"_id":"5db9a9b7973fac39d8d48512","username":"devel","email":"devel@viewtinet.com","name":"Developer","lastname":"","access_token":"eyJhbG...","expiresIn":3600000}
```

Note that the same endpoint can be reached via https on port 4001:<br />
`https://192.168.1.187:4001/auth/login`

If authentication has been successful, `access_token` must be stored and used in following API calls in order to accept both GET and POST requests. The same way, cipher can be used as auth url param when accessing frontend, as explained in the Viewtisight Integration chapter.

<br />

## **Set Requests**

The sequence to request sets is as follows:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img4.png" align="center"></figure>

<br />

This is an example of how to get sets using `curl` command:

```bash
curl -X GET "http://192.168.1.199:4101/data/sets" -H "accept: /" -H "authorization: bearer eyJhb..."
```

**Response Example:**

```json
{"idrequest":"a2976ca1-8846-47bb-bd21-3cde4cb8e877","sets":["dpi_records","pcap_storage_records"]}
```

In the prior example, there would be two sets: `dpi_records` and `pcap_storage_records` that can be queried.

<br />

## **Set fields requests**

The sequence to request fields for a given set is as follows:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img5.png" align="center"></figure>

<br />

Fields will contain the following attributes:

-   `type` → Object Type: `STRING`, `ULONG`, `LONG`, `IPADDRESSV6`, `IPADDRESSV4`, `UINT`, `INT`, `DOUBLE`
-   `name` → field name

This is an example of how to get set fields using `curl` command:

```bash
curl -X GET "http://192.168.1.171:4101/data/dpi_records/fields" -H "accept: /" -H "authorization: bearer eyJhb..."
```

**Response Example:**

```json
{"err":"Success","idrequest":"...","set":"dpi_records","fields":[{"type":"STRING","name":"app_name"},{"type":"ULONG","name":"connection_time"},...]}
```

In the prior example, these would be the list of fields and metadata for `dpi_records` set. Having the list of fields allows external integrations to create data requests in the proper query format.

<br />

## Reports/KQIs requests

The sequence to request reports is as follows:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img6.png" align="center"></figure>

<br />

This call will return the list of all reports available in the system. Here is an example using `curl` command:

```bash
curl -X GET "http://192.168.1.171:4101/queryobjects" -H "accept: /" -H "authorization: bearer eyJhb..."
```

If only reports for a specific set are needed, there is another call:<br />
`http://&lt;VIEWTISIGIHT_AP_ADDRESS&gt;/queryobjects/&lt;set&gt;`

Here is an example using `curl` command:

```bash
curl -X GET "http://192.168.1.171:4101/queryobjects/dpi_records" -H "accept: /" -H "authorization: bearer eyJhb..."
```

<br />

## **Dashboard requests**

The sequence to request dashboards is as follows:

This call will return the list of all dashboards available in the system. Here is an example using `curl` command:

```bash
curl -X GET "http://192.168.1.171:4101/dashboards" -H "accept: /" -H "authorization: bearer eyJhb..."
```

Dashboards are useful as they have predefined queries with some meaning (e.g., Dashboard for network performance) and allow integrations to perform queries just by grabbing the dashboard response. If dashboards are not defined, the user will have to combine set metadata and set reports to retrieve data.

<br />

## **Data requests**

Viewtisight stores information in both raw records (usually millions of records) and aggregated ones in order to speed up queries. However, only raw tables are shown and aggregated tables are internal as they are used automatically by the system depending on incoming query. That is, there is a query scheduler evaluating which table is the best that can return results in the fastest and complete way being this process transparent to users.

These are the parameters to perform data request, using query format:

-   `fields`
    
    -   `list`: list of fields to retrieve with any aggregation operation. They are used to get all records from tables without any kind of grouping or aggregation.
-   `filters`: list of filters to perform over columns in tables (e.g., filter by some specific IP Address).
-   `group`
    
    -   `list`: list of fields to retrieve applying aggregation and grouping operations. There are 3 kind of group list fields:
    -   `dimension`: string columns that will be using for grouping reports (e.g., source ip address).
    -   `metric`: numeric column that will apply some aggregation operation (e.g., SUM).
    -   `calculated`: combination of metric fields or constant values to perform advanced mathematical operations.
-   `filters`: list of filters to perform over an already aggregated records (e.g., filter records with a SUM(column) greater than 1000).
-   `order`
    
    -   `list`: list of order fields to perform order operation. Ascending and Descending order are supported for any kind of column.
-   `limit`: Operation to limit results. Useful to get top/bottom elements or iterate over a paginated table.
-   `offset`: offset to start returning records.
-   `count`: number of records to return.
-   `timerange`: time ranges for query.
    
    -   `start`: timestamp used to start for lookup.
    -   `end`: timestamp used to finish lookup.
    -   `timefield`: field used to perform temporal lookup.
-   `size`: true/false value. If true, number of records returned by query are available in response.
-   `granularity`: used to receive records in time-series format.
    
    -   `value`: value of time bucket.
    -   `unit`: unit in which value is set. These are the values available:
    -   second
    -   minute
    -   hour
    -   week
    -   day
    -   year

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img7.png" align="center"></figure>

<br />

### **Examples**

Here are some examples of queries performed used with set `dpi_records`, which contains statistics extracted by Viewtimon DPI:

#### Total Volume (Network)

```bash
curl 'http://192.168.1.200:4101/data/dpi_records/query' \
  -H 'Authorization: bearer eyJhb...' \
  -H 'Content-Type: application/json' \
  --data-raw '[{"type":"main","vals":{"size":false,"fields":{},"group":{"list":[{"calculated":{"name":"total_bytes","operation":"add","fields":[{"metric":{"name":"volume_downlink","operation":"sum"}},{"metric":{"name":"volume_uplink","operation":"sum"}}]}}]},"limit":{"seriesFilter":10},"granularity":{"value":"1","unit":"minute"},"subqueries":[],"subQueriesOperator":"","alias":"","timerange":{"start":"1697013960000000","end":"1697017559999999","timefield":"timestamp"},"order":{"list":[{"name":"timestamp","order":"asc"},{"name":"total_bytes","order":"desc"}]},"allowDimensions":true,"isTimeSeries":true}}]' \
  --compressed
```

#### Total Volume by app

```bash
curl 'http://192.168.1.200:4101/data/dpi_records/query' \
  -H 'Authorization: bearer eyJhb...' \
  -H 'Content-Type: application/json' \
  --data-raw '[{"type":"main","vals":{"size":false,"fields":{},"group":{"list":[{"dimension":{"name":"app_name","alias":"app_name"}},{"calculated":{"name":"total_bytes","operation":"add","fields":[{"metric":{"name":"volume_downlink","operation":"sum"}},{"metric":{"name":"volume_uplink","operation":"sum"}}]}}]},"limit":{"count":10,"seriesFilter":10},"granularity":{"value":1,"unit":"minute"},"subqueries":[],"subQueriesOperator":"","alias":"","timerange":{"start":"1697013960000000","end":"1697017559999999","timefield":"timestamp"},"order":{"list":[{"name":"total_bytes","order":"desc"},{"name":"app_name","order":"asc"}]},"allowDimensions":true,"isTimeSeries":false}}]' \
  --compressed
```

#### Total Volume by app “youtube”

```bash
curl 'http://192.168.1.200:4101/data/dpi_records/query' \
  -H 'Authorization: bearer eyJhb...' \
  -H 'Content-Type: application/json' \
  --data-raw '[{"type":"main","vals":{"size":false,"fields":{"filter":{"logical":{"operator":"and","expressions":[{"comparison":{"name":"app_name","fieldType":"string","operator":"eq","value":"\'youtube\'"}}]}}},"group":{"list":[{"dimension":{"name":"app_name","alias":"app_name","cast":""}},{"calculated":{"name":"total_bytes","operation":"add","fields":[{"metric":{"name":"volume_downlink","operation":"sum"}},{"metric":{"name":"volume_uplink","operation":"sum"}}]}}]},"limit":{"count":10,"seriesFilter":10},"granularity":{"value":5,"unit":"minute"},"subqueries":[],"subQueriesOperator":"","alias":"","timerange":{"start":"1697014200000000","end":"1697017799999999","timefield":"timestamp"},"order":{"list":[{"name":"total_bytes","order":"desc"},{"name":"app_name","order":"asc"}]},"allowDimensions":true,"isTimeSeries":false}}]' \
  --compressed
```

<br />

## **Logout**

The logout process invalidates the current session token.

This is an example of how to perform a logout using the `curl` command:

```bash
curl -X POST "http://<VIEWTISIGHT_IP>:4000/auth/logout" \
  -H "Accept: /" \
  -H "Content-Type: application/json" \
  -H "Authorization: bearer <TOKEN>"
```

<br />

## **Python Integration Example**

The following is a complete Python script example based on the methods explained in this guide. This script demonstrates how to authenticate, retrieve data (in this example, fetching the available sets), save the response, and finally log out securely.

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