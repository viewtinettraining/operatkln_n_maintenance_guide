---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Início'
id: MPA-ENWC-B5Z-BG4
slug: home
isVisible: true
isSearchable: true
lastUpdated: '2026-09-10 19:54:49'
---
# **<span align="center">Painel Inicial (Home Dashboard)</span>**

<br />

Esta é a página inicial padrão após o login, fornecendo uma visão geral rápida do desempenho do sistema.

## **✅ Integridade do Sistema (System Health)**

Indicadores visuais confirmam que o sistema está funcionando normalmente e sem problemas.

Uma caixa verde com um ícone de polegar para cima indica o status saudável.

O carimbo de data/hora da última verificação do sistema é exibido.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/fB2lew9q7QQ0F769bEfx.png"></figure>

<br />

## **📌 Menu Suspenso de Visualizações do Painel**

<br />

A partir do painel inicial (Home), os usuários podem alternar entre os seguintes painéis de monitoramento:

-   **Desempenho do Cluster (Cluster Performance)**
-   **Monitoramento de Disco (Disk Monitoring)**
-   **Monitoramento de Logins de Usuários (Monitoring Users Logins)**
-   **Verificação de Integridade do Disco (opção listada, não mostrada nas imagens)**
-   **Cada visualização fornece monitoramento direcionado dependendo do tema selecionado.**
    
    <br />
    

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/yZuwyc9Q4aXaGFlZXu00.png"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/dNijd5Ni6JW7bzcov4rY.png" align="center"></figure>

<br />

## **📊 Desempenho do Cluster (Cluster Performance)**

<br />

Gráficos em tempo real com métricas coletadas do cluster, incluindo:

-   Uso de CPU:
    
    -   Detalhamento por User, System, Wait e Nice
-   Uso de Memória:
    
    -   Porcentagem de memória utilizada
-   Número de Processos:
    -   Processos ativos do sistema ao longo do tempo
-   Rede:
    
    -   Taxa de transferência de entrada e saída (Mbps) no nó

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/0MpfuRYMlkdLqpgpaUpN.png" align="center"></figure>

<br />

## **💽 Monitoramento de Disco (Disk Monitoring)**

Acessível através de um menu suspenso na exibição do painel, este painel fornece métricas relacionadas a disco por partição:

-   Uso Total do Disco:
    
    -   Exibido em porcentagem e em gigabytes
-   IOPS de Leitura / IOPS de Gravação:
    
    -   Operações de entrada/saída por segundo por partição
    -   Read Await / Write Await:
    -   Latência em milissegundos para operações de leitura/gravação
-   Filtros de Tempo Disponíveis:
    
    -   Data inicial e final
    -   Atalho de tempo (por exemplo, “Último dia”)
    -   Granularidade (por exemplo, 5 minutos)

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/dJbEPWPk39uUNLIH2FHs.png" align="center"></figure>

<br />

## **👥 Monitoramento de Logins de Usuários**

Esta seção permite que os administradores revisem o acesso à plataforma pelos usuários.

-   Gráfico de Logins:
    
    -   Gráfico de barras mostrando contagens de login por usuário (por exemplo, admin)
-   Tabela de Horários de Login dos Usuários:
    
    -   Exibe nomes de usuário com seus respectivos carimbos de data/hora
-   Linha do Tempo de Login:
    
    -   Gráfico de séries temporais da atividade de login
    -   Útil para:
    -   Auditoria de acesso à plataforma
    -   Acompanhamento da frequência de login e janelas de tempo

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/Dpf2IKLcxU1gk5TbQbEO.png" align="center"></figure>

<br />

## **✅ Resumo**

<br />

O módulo Viewtimanager fornece acesso centralizado para:

Status de integridade do sistema e métricas de desempenho

Monitoramento de latência e uso de disco

Auditoria de acesso de usuários

Navegação para todos os principais componentes da plataforma Viewtinet

É a interface fundamental para os administradores manterem a estabilidade da plataforma, auditarem atividades e garantirem a continuidade dos serviços.
