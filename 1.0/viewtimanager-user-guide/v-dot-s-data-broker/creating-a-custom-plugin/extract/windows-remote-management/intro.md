---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Intro
id: SOU-4DMA-MVG-KSA
slug: intro
isVisible: true
lastUpdated: '2025-09-04 12:44:22'
---
# **<span align="center">Gerenciamento Remoto do Windows (WinRM)</span>**

<br />

O **Conector de Gerenciamento Remoto do Windows (WinRM)** permite que o Viewtilog se conecte com segurança a servidores Windows e recupere uma ampla gama de métricas de desempenho, logs e informações do sistema.<br />
Ao aproveitar o **protocolo nativo WinRM** da Microsoft, este conector fornece monitoramento sem agente, eliminando a necessidade de instalação de software adicional nos hosts Windows de destino.

<br />

## **Principais Recursos**

-   **Métricas de Desempenho**: Coleta contadores como a utilização da CPU, uso da memória, E/S (I/O) de disco e estatísticas de rede.
-   **Informações do Sistema**: Reúne detalhes que incluem o tempo de atividade, processos em execução, hotfixes instalados e configuração do sistema.
-   **Logs de Eventos**: Consulta logs de eventos do Windows (ex., Segurança, Aplicativo, Sistema) para eventos específicos como tentativas de logon, mudanças de estado de serviços ou erros.
-   **Acesso sem Agente**: Usa o WinRM via HTTP/HTTPS para se comunicar, garantindo sobrecarga mínima no sistema monitorado.

<br />

## **Casos de Uso Típicos**

-   Monitoramento do consumo de recursos de servidores Windows críticos.
-   Coleta de eventos de logon e segurança a partir de controladores de domínio.
-   Rastreamento do uso do disco e desempenho em servidores de aplicativos.
-   Auditoria de configuração e de integridade do sistema sem implementação de agentes adicionais.

<br />

📌 O Conector WinRM é ideal para organizações com infraestruturas baseadas em Windows, pois se integra perfeitamente ao pipeline ETL do Visual Smart Data Broker (VSDB) com o objetivo de fornecer visibilidade da integridade do servidor e dos eventos de segurança em tempo real.