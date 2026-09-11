---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Sflow
id: Z4I-P8Q4-K1D-88D
slug: sflow
isVisible: true
lastUpdated: '2025-09-02 15:11:06'
---
# **<span align="center">Conector sFlow</span>**

<br />

O **Conector sFlow** é projetado para processar dados de fluxo exportados no **protocolo sFlow** de dispositivos de rede como switches e roteadores. Semelhante ao Conector NetFlow, ele funciona em conjunto com o pipeline **Ethernet Streamer**. Antes de usar este conector, é **obrigatório** configurar um pipeline **Ethernet Streamer** com a porta correta (geralmente UDP/6343) e os filtros de host. O Ethernet Streamer captura o tráfego sFlow binário e o armazena no diretório do **Caminho Coletado (Collected Path)**, onde o Conector sFlow os processa e decodifica posteriormente.

<br />

⚠️ **Nota:** O Viewtinet fornece um **Template de Plugin** para integrações sFlow. Na maioria dos cenários, você não precisará configurar este conector manualmente, pois o template já inclui uma configuração funcional.

<br />

## **Principais Parâmetros**

-   **Tipo de Frequência**<br />
    O mesmo que os outros conectores agendados (ICMP, SNMP, CSV, NetFlow). Pode ser configurado como:
    
    -   **Periódico**: Executa a cada _x_ segundos (definidos em _Tempo de Atualização_).
    -   **Agendado**: Executa de acordo com uma Expressão Cron.
-   **Threads**<br />
    Define o número de threads simultâneas para execução do pipeline. Aumentar esse número permite que mais arquivos sejam processados simultaneamente, mas também aumenta o uso da CPU e da memória.
-   **Caminho Coletado (Collected Path)**<br />
    Diretório onde o Ethernet Streamer despeja os arquivos de tráfego sFlow capturados.
-   **Caminho de Processamento (Processing Path)**<br />
    Diretório temporário onde os arquivos são manuseados durante a decodificação.
-   **Caminho Processado (Processed Path)**<br />
    Diretório onde os arquivos são armazenados após o processamento bem-sucedido.
-   **Sufixo**<br />
    Extensão de arquivo dos arquivos despejados, geralmente `.csv` ou um formato binário, dependendo da configuração.
-   **Máx de Arquivos**<br />
    Número máximo de arquivos processados por thread durante cada ciclo de execução.
-   **Número de Execuções**
    
    -   `-1`: O conector funcionará indefinidamente.
    -   Inteiro positivo: Limita a execução ao número especificado de execuções.
-   **Versão**<br />
    Define como os campos são decodificados de acordo com a versão padrão sFlow. Normalmente suporta **sFlow v5**, que é o mais amplamente usado.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/XgZ5Nqi9RM1DUarAFCdd.png"></figure>

<br />