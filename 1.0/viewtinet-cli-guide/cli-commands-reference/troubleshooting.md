---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Troubleshooting
id: XRV-WRYD-2NW-IYL
slug: troubleshooting
isVisible: true
lastUpdated: '2025-10-15 16:09:54'
---
# **<span align="center">Script de Solução de Problemas (Troubleshooting)</span>**

O script `troubleshooting.sh` é uma ferramenta de diagnóstico abrangente projetada para implantações da Viewtinet em execução em servidores Ubuntu. Seu principal objetivo é automatizar a verificação de saúde dos recursos centrais do sistema e dos módulos de microsserviços da Viewtinet. Ele verifica a disponibilidade dos contêineres, logs, uso de disco e memória, arquivos de configuração, saúde do banco de dados e muito mais.

Este script é especialmente útil para verificações programadas por meio de tarefas cron, fornecendo recursos de geração de alarmes e salvamento de logs para rastreamento e alertas de longo prazo.

Ele suporta os seguintes módulos:

-   **System**: saúde geral da CPU, memória, partições, interfaces.
-   **Viewtimanager**: verificações do frontend, backend, banco de dados e rede.
-   **Viewticore**: componentes internos e uso de armazenamento.
-   **Viewtisight**: disponibilidade de serviços e endpoints.
-   **Viewtiauth**: validações de contêiner e rede.
-   **Bypasser**: estado do dispositivo e integridade do plugin.
-   **Viewtimon**: verificações de log, configuração e pipelines.
-   **Sniffer**: partição pcap e serviços de captura ao vivo.
-   **Dhyana**: processamento de conectores, frescor dos dados e pipelines.
-   **HA**: verificações de replicação do PostgreSQL e consistência do cluster.

<br />

## **Uso**

### **Uso Básico**

```bash
$ sudo  /opt/vn/viewtinet-builder/scripts/troubleshooting.sh
```

Isso executará todas as verificações e emitirá um resumo de saúde global.

### Sinalizadores Opcionais (Flags)

```bash
  -h | --help                         Show help message
  -l | --logging <directory>          Enable logging to given directory
  -a | --alarms <directory>           Enable alarm output as CSV (for Self Monitoring plugin ingestion)
  -d | --dhyana-csv-dir <directory>   Enable Dhyana pipeline stats to CSV (used by dashboard plugin)
  -t | --time-inteval <mins>          Set time interval in minutes for log checks
  -p | --parallel-jobs <num>          Max parallel jobs (default: 5)
  --dhyana-logs                       Enable pipeline log checking (can be slow with many pipelines)
  --dhyana-files                      Check data folder in /opt/vn/dhyana/var/data/ (verbose, optional)
```

<br />

## **Seleção de Módulo**

Você pode especificar módulos individuais para verificação:

```bash
sudo  /opt/vn/viewtinet-builder/scripts/troubleshooting.sh dhyana
```

Para verificar apenas a saúde do sistema:

```bash
sudo  /opt/vn/viewtinet-builder/scripts/troubleshooting.sh system
```

<br />

## **Recursos de Exportação de Alarmes e Dhyana**

### Geração de Alarmes (`-a`)

Quando executado com a opção `-a`, o script ativará a geração de alarmes e emitirá um arquivo CSV compatível com o plugin **Self Monitoring** da Viewtinet. Isso permite a ingestão automática de status do sistema e de módulos como alarmes estruturados.

O arquivo CSV de saída inclui:

-   Timestamp (Data e hora)
-   Nome do alarme
-   Severidade (clear, minor, major, critical)
-   Descrição

Isso possibilita uma integração perfeita com dashboards de alarmes e regras de alerta.

<br />

## **Estatísticas de Pipeline do Dhyana (**`-d`**)**

A opção `-d` habilita uma exportação avançada de **métricas de status de pipeline do Dhyana** para um arquivo CSV no diretório especificado. Este arquivo é projetado para ingestão pelo plugin **Dhyana Dashboard** e é normalmente usado para gerar gráficos e relatórios sobre a saúde do pipeline.

Os dados incluem:

-   Nome e PID do pipeline
-   Status da execução
-   Contagem de erros nos logs (se `--dhyana-logs` estiver habilitado)

> ⚠️ Isso é útil para análise de desempenho, mas habilitar `--dhyana-logs` pode retardar a execução em ambientes com muitos pipelines.

<br />

## **Verificações Profundas Opcionais**

-   `--dhyana-logs`: Varredura profunda dos logs do contêiner Dhyana para extrair erros relacionados ao pipeline. Isso aumenta a precisão, mas aumenta o tempo de execução, especialmente em ambientes com muitos pipelines concorrentes.
-   `--dhyana-files`: Habilita a verificação de cada subdiretório em `/opt/vn/dhyana/var/data/` para detectar arquivos inativos ou superdimensionados. Esta verificação é detalhada e deve ser usada seletivamente.

<br />