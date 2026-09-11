---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Tarefa Python'
id: G0B-9DU5-VOF-55K
slug: python-task
isVisible: true
lastUpdated: '2025-09-03 10:30:56'
---
# **<span align="center">Conector Python Task</span>**

O **Conector Python Task** permite aos usuários integrarem programas Python customizados no Visual Smart Data Broker (VSDB). Por meio desse conector, é possível coletar métricas, logs ou qualquer outro tipo de dado de fontes acessíveis via código Python.

Isso fornece uma maneira flexível de estender as integrações do Viewtinet quando não há um conector padrão disponível. A Tarefa Python executa os scripts desenvolvidos pelo usuário e transforma suas saídas em registros compatíveis com o banco de dados de série temporal do Viewtinet.

---

## **Criando seu Programa Python**

Para usar o Conector Python Task, você deve criar um programa Python no seguinte diretório do servidor Viewtilog:

```bash
/opt/vn/dhyana/bin
```

Seu script deve seguir um template predefinido para ser compatível com o Python Loader.

```python
import sys
sys.path.append('/app/python-modules/')
from bin.data_wrapper import DataWrapper
import os
import warnings
warnings.filterwarnings('ignore')

_config: dict = None

def init(config: dict):
    global _config
    _config = config
    # Exemplo: endpoint = _config.get("endpoint")

def read() -> DataWrapper:
    global _config
    # Implemente sua lógica aqui
    data = DataWrapper.wrap(SEU_DICIONARIO)
    return data
```

<br />

### **Exemplo: Coletando o Uso da CPU do Linux em** `/proc/stat`

<br />

O script a seguir lê as estatísticas de uso da CPU a partir do arquivo `/proc/stat`, calcula a porcentagem de utilização da CPU, e retorna isso junto de um carimbo de data/hora. Este script pode ser salvo em `/opt/vn/dhyana/bin/cpu_monitor.py`.

<br />

```python
import sys
sys.path.append('/app/python-modules/')
from bin.data_wrapper import DataWrapper
import os
import warnings
import time

warnings.filterwarnings('ignore')

_config: dict = None

def init(config: dict):
    global _config
    _config = config

def read() -> DataWrapper:
    # Obtém o timestamp atual em milissegundos
    timestamp = int(time.time()  1000000)

    # Lê estatísticas de CPU do /proc/stat
    with open("/proc/stat", "r") as f:
        line = f.readline()
    parts = line.split()

    # Extrai tempos user, nice, system, idle
    user, nice, system, idle = map(int, parts[1:5])

    # Calcula o total e o percentual de uso
    total = user + nice + system + idle
    busy = total - idle
    cpu_usage_percent = (busy / total)  100 if total > 0 else 0

    # Prepara o dicionário de saída
    result = [
        {
            "timestamp": timestamp,
            "cpu_usage": round(cpu_usage_percent, 2)
        }
    ]

    # Envolve o dicionário num DataWrapper
    return DataWrapper.wrap(result)
```

<br />

### **Saída de Exemplo**

Se executado em tempo de execução, o conector pode produzir registros como:

```json
[
  {
    "timestamp": 1756894500328,
    "cpu_usage": 6.79
    
  }
]
```

-   `timestamp`: Campo obrigatório em milissegundos.
-   `cpu_usage`: O percentual medido de uso da CPU.

<br />

### **Resumo do Fluxo de Trabalho**

1.  Salve seu script em `/opt/vn/dhyana/bin`.
2.  Garanta que ele siga o template do Python Loader (funções `init` + `read`).
3.  Implemente sua lógica dentro do método `read()`.
4.  Retorne os dados como uma lista de dicionários contendo pelo menos um campo **timestamp**.

<div data-start="3573" data-end="3752"><p><br></p><div class="sd-callout" data-callout-type="alert"><strong>Importante</strong><br>O programa Python deve sempre retornar os dados com um campo <strong>timestamp</strong> (em microssegundos, 16 dígitos). Sem isso, os registros não poderão ser armazenados no banco de dados de série temporal do Viewtinet.</div></div>

<br />

Uma vez que você desenvolveu e salvou o script Python no caminho `/opt/vn/dhyana/bin`, o próximo passo será configurar o **Estágio Extract** (Extração) no seu pipeline. Esta etapa faz a ligação entre o código Python que você criou e o processo ETL do Viewtinet.

<br />

## **Passo 2: Configurando o Estágio Extract**

Siga estes passos para configurar o Conector Python Task:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/7Vf0zAE1kKRxoz8feGg4.png" align="center" data-drop-shadow="disabled"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/qFQTZidQxXU9zroD8VWH.png" align="center"></figure>

<br />

1.  **Selecione o Tipo de Conector**<br />
    No menu suspenso, escolha **Python Task Connector**.
2.  **Nome do Pipeline**<br />
    Insira um nome único para o pipeline. Exemplo: `my_python_task`.
3.  **Configuração de Execução**
    
    -   Escolha o **Tipo de Frequência**: `Agendado` (Scheduled) ou `Periódico` (Periodic).
    -   Defina a **Expressão Cron** ao utilizar a execução agendada (ex., a cada minuto).
    -   Configure o **Número de Execuções**:
        
        -   `-1` significa uma execução infinita.
        -   Qualquer inteiro positivo vai limitar a quantidade de vezes que a tarefa será executada.
4.  **Caminho do Programa**<br />
    Determine o diretório no qual o seu script Python está salvo; normalmente:<br />
    `/opt/vn/dhyana/bin/`
5.  **Nome do Módulo**<br />
    Insira o nome de seu arquivo Python (omitindo a extensão `.py`).<br />
    Exemplo: em `cpu_monitor.py`, você deverá colocar `cpu_monitor`.
6.  **Função Principal**<br />
    Especifique a função que será executada de dentro do script. Por convenção, deve ser a `read`.
7.  **Argumentos (Opcional)**<br />
    Se o script Python requerer a passagem de parâmetros, você poderá defini-los aqui mediante uma configuração de chaves **nome** (name) e **valor** (value). Eles serão então transmitidos ao seu script em tempo de execução.
8.  **Defina os Campos de Saída**
    
    -   Adicione os campos que seu script Python retornará.
    -   **Campo obrigatório:** `timestamp` → o tipo deve ser `ulong`.
    -   Defina os campos adicionais conforme a necessidade (ex., `cpu_usage`, `memory_usage`, etc.).
    -   Esses campos deverão bater com as chaves do dicionário de dados gerado por seu script Python.

✅ Configuração de Exemplo:

-   **Nome do Campo:** `timestamp` → **Tipo de Campo:** `ulong`
-   **Nome do Campo:** `cpu_usage` → **Tipo de Campo:** `ulong`

<br />

<br />