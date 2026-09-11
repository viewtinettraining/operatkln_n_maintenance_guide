---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'NetFlow'
id: N8H-HPYX-VSJ-1GV
slug: netflow
isVisible: true
lastUpdated: '2025-09-02 12:36:00'
---
# **<span align="center">Netflow</span>**

O **Conector Netflow** foi projetado para processar dados de fluxo (Netflow, JFlow, NetStream) capturados pelo pipeline do **Ethernet Streamer**. Antes de usar este conector, é **obrigatório** configurar um pipeline **Ethernet Streamer** válido com os filtros de porta e host corretos. O Ethernet Streamer captura o tráfego binário e o armazena no diretório do **Caminho Coletado** (Collected Path), onde o Conector Netflow o processará e decodificará posteriormente.

<br />

⚠️ **Nota:** O Viewtinet já fornece um **Template de Plugin** para integrações de Netflow, portanto, na maioria dos casos, você não precisará configurar este pipeline manualmente.

<br />

## **Principais Parâmetros**

-   **Tipo de Frequência**<br />
    Funciona da mesma forma que os outros conectores agendados (ICMP, SNMP, CSV). Ele pode ser definido como:
    
    -   **Periódico**: Executa a cada _x_ segundos definidos no _Tempo de Atualização_.
    -   **Agendado**: Executa com base em uma Expressão Cron.
-   **Threads**<br />
    Define o número de threads simultâneas para execução do pipeline. Aumentar o número de threads permite processar vários arquivos simultaneamente, mas também aumentará o uso de CPU e memória. Ajuste cuidadosamente dependendo dos recursos do sistema.
-   **Caminho Coletado (Collected Path)**<br />
    Diretório onde o Ethernet Streamer despeja os arquivos de tráfego Netflow capturados.
-   **Caminho de Processamento (Processing Path)**<br />
    Local temporário onde os arquivos são processados.
-   **Caminho Processado (Processed Path)**<br />
    Diretório onde os arquivos são armazenados após serem processados ​​com sucesso.
-   **Sufixo**<br />
    Extensão de arquivo dos arquivos despejados, geralmente `.csv`.
-   **Máx de Arquivos**<br />
    Número máximo de arquivos a serem lidos por execução de thread. Por exemplo, se for definido como `5` e houver 3 threads, o conector poderá processar até 15 arquivos em paralelo.
-   **Número de Execuções**<br />
    Se definido como `-1`, o pipeline será executado continuamente. Qualquer outro valor especifica o número de execuções antes de parar.
    
    <br />
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/EgT0xLm3xxAsC58zkY5T.png" align="center"></figure>

<br />

-   **Versão**<br />
    Define a versão do Netflow a ser usada para decodificar os registros. As versões suportadas incluem **5**. **9 e IPFIX**.<br />
    A versão selecionada determina quais campos serão decodificados e armazenados.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/dRHicKbWSX5sCewcL6gx.png"></figure>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/X9ZU8iol52d7WRzNEy2H.png"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/mI049ZPsaejF8gWwjxdZ.png" align="center"></figure>

<br />

Cada campo está vinculado à versão Netflow selecionada (v5, v9 ou IPFIX). Garanta consistência entre a versão configurada e o conjunto de campos esperado.

<br />

✅ Com este conector, o Viewtinet transforma as exportações brutas do Netflow em dados estruturados prontos para monitoramento, dashboards e análises.

<br />