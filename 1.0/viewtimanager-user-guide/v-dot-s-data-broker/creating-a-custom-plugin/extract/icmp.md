---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'ICMP'
id: NTA-4FAZ-5QN-QO6
slug: icmp
isVisible: true
lastUpdated: '2025-10-15 15:26:24'
---
# **<span align="center">Conector ICMP</span>**

<br />

O **Conector ICMP** permite que o Visual Smart Data Broker (VSDB) realize verificações de integridade em dispositivos usando **ping (echo requests)**. Ele é comumente usado para monitorar a acessibilidade de rede e as taxas de perda de pacotes em servidores, roteadores, switches e outros dispositivos com IP.

<br />

## **Acessando o Conector ICMP**

1.  A partir do **Criador de Plugins**, selecione o estágio **Extract**.
2.  Na lista de conectores, escolha **Conector ICMP**.
3.  A tela de configuração do Conector ICMP será exibida.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/4kFBZNWQnWiH3RD9afaf.png" align="center"></figure>

<br />

## **Parâmetros de Configuração**

-   **Tipo de Frequência**<br />
    Define a frequência com que o conector é executado:
    
    -   **Periódico**: O pipeline é executado pela primeira vez após o número configurado de segundos (Tempo de Atualização) assim que o plugin for instalado, e continua se repetindo nesse intervalo.
    -   **Agendado**: A execução é definida usando uma **expressão cron**, permitindo um agendamento preciso por minuto, hora, dia, semana ou mês.
-   **Número de Execuções**
    
    -   `-1`: O conector roda indefinidamente.
    -   Qualquer valor positivo: O pipeline é executado exatamente esse número de vezes.
-   **Sessão**<br />
    Um parâmetro de string obrigatório usado internamente pelo módulo para rastrear a execução.
-   **Contagem de Ping**<br />
    Define o número de **solicitações de eco** (pings) enviados a cada host durante cada ciclo de execução.
    
    -   Para que um host seja declarado como **inativo (down)**, _todas_ as solicitações de eco devem falhar.
    -   A porcentagem de perda de pacotes é calculada como:
        
        ```
        Pacotes perdidos / Contagem de Ping * 100
        ```
        
        Exemplo:
        
        -   Se `Contagem de Ping = 5` e 1 ping for perdido → perda de pacotes = 20%.
        -   Se `Contagem de Ping = 4` e 1 ping for perdido → perda de pacotes = 25%.
-   **Tempo Limite (Timeout) do Ping**<br />
    O tempo máximo de espera (em segundos) por cada resposta de eco. Se o host não responder dentro desse tempo, o ping será considerado perdido.
-   **Tamanho do Lote de Hosts**<br />
    Define quantos hosts são pingados simultaneamente em cada lote.
    
    -   Exemplo: Se houver **100 hosts** no conector e `Tamanho do Lote de Hosts = 50`, o sistema cria **2 pipelines**, cada um lidando com 50 hosts em paralelo.

<br />

## **Seção de Hosts**

Pelo menos um host deve ser definido no conector.<br />
Os hosts podem ser provisionados de duas maneiras:

-   **Provisionamento em massa via Inventário** (recomendado para grandes ambientes, consulte o capítulo de _Inventário_).
-   **Entrada manual** usando o botão **Adicionar Host**, onde você especifica o endereço IP e outros detalhes.

Os hosts também podem ser importados ou exportados usando os botões disponíveis na interface.

<br />

## **Resumo**

O Conector ICMP permite o monitoramento de acessibilidade e latência de dispositivos por meio de operações de ping configuráveis:

-   Suporta modos de execução **Periódico** e **Agendado**.
-   Mede a **porcentagem de perda de pacotes** baseada na Contagem de Ping configurada.
-   Requer falha total da solicitação de eco para marcar um host como **inativo (down)**.
-   O **Tamanho do Lote de Hosts** garante monitoramento escalável em grandes ambientes, dividindo os hosts em grupos.

A configuração correta assegura verificações de disponibilidade precisas e o uso eficiente dos recursos do sistema.