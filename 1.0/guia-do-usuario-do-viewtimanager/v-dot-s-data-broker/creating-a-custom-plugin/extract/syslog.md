---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Syslog'
id: 9KD-EY7D-1I9-Y1X
slug: syslog
isVisible: true
lastUpdated: '2025-09-03 16:25:58'
---
# **<span align="center">Conector Syslog</span>**

O **Conector Syslog** é utilizado para processar mensagens de syslog que foram previamente capturadas pelo conector **Ethernet Streamer**. Semelhante ao conector Netflow, ele opera como um **pipeline agendado**, o que significa que é executado periodicamente com base na frequência de execução configurada.

Ao contrário do Netflow, o protocolo Syslog não requer a seleção de uma versão, o que simplifica sua configuração.

<br />

## **Principais Características**

-   Funciona em conjunto com o pipeline **Ethernet Streamer**, o qual despeja o tráfego syslog bruto num diretório específico.
-   Processa periodicamente os arquivos despejados e extrai as mensagens de syslog.
-   Cada registro de syslog é então convertido em campos estruturados para posterior análise.
-   Altamente escalável, pois múltiplas threads podem ser configuradas para processamento simultâneo.

## **Parâmetros de Configuração**

A partir da captura de tela fornecida:

1.  **Tipo de Conector**<br />
    Selecione **Syslog Connector** como o tipo de conector.
2.  **Nome do Pipeline**<br />
    Defina um nome único para o pipeline (ex., `my_syslog_connector`).
3.  **Número de Threads**<br />
    Configure o número de threads simultâneas.
    
    -   Mais threads = processamento mais rápido.
    -   Contudo, valores mais altos aumentam o consumo de CPU e memória.
4.  **Configuração de Execução**
    
    -   **Tipo de Frequência**: Agendado ou periódico.
    -   **Expressão Cron**: Define com que frequência o pipeline será executado (ex., a cada minuto).
    -   **Número de Execuções**: `-1` indica execuções ilimitadas.
5.  **Caminhos**
    
    -   **Caminho Coletado (Collected Path)**: Diretório onde o Ethernet Streamer despeja o tráfego syslog bruto.
    -   **Caminho de Processamento (Processing Path)**: Diretório temporário usado durante o processamento dos arquivos.
    -   **Caminho Processado (Processed Path)**: Diretório final onde os arquivos processados são armazenados.
6.  **Manipulação de Arquivos**
    
    -   **Sufixo**: Define o formato dos arquivos a serem processados (ex., `.csv`).
    -   **Máx de Arquivos**: Número máximo de arquivos a serem lidos por ciclo de execução.
    -   **Tamanho do Bloco (Chunk Size)**: Divide arquivos grandes em partes menores para um processamento mais eficiente.
        
        <br />
        

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/M6zx6jJzAjbqb3WU5xu0.png" align="center"></figure>

## **Cenário de Exemplo**

Se o **Ethernet Streamer** for configurado para capturar tráfego syslog de vários dispositivos na porta 514 e despejar os dados em `/opt/vn/dhyana/var/data/syslog/collected`, então o Conector Syslog irá:

1.  Ler periodicamente os arquivos desse diretório.
2.  Processar e decodificar as mensagens syslog.
3.  Armazenar a saída estruturada no diretório processado para uso em etapas posteriores do pipeline ETL.

---

> ⚠️ **Nota Importante**<br />
> O Conector Syslog **depende de um pipeline Ethernet Streamer devidamente configurado**. Sem ele, não haverá tráfego para ser processado.

<br />