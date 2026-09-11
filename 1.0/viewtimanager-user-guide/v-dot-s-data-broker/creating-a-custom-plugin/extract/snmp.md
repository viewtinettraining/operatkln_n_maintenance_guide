---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: SNMP
id: GE5-DPO8-5AX-W06
slug: snmp
isVisible: true
lastUpdated: '2025-09-02 09:43:03'
---
# **<span align="center">Conector SNMP</span>**

<span align="justify">Esta subseção explica como configurar o estágio Extract de um plugin utilizando o Conector SNMP. O Conector SNMP é um dos conectores mais comuns disponíveis no Visual Smart Data Broker (VSDB), permitindo a aquisição de dados de dispositivos de rede, servidores e de qualquer sistema que suporte o protocolo SNMP.</span>

<br />
**Acessando o Estágio Extract**

1.  A partir do **Criador de Plugins**, selecione o estágio **Extract**.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/R1CROHlmnYMpjiXd0AYc.png" align="center"></figure>
    
2.  Clique no **ícone de seleção de conector** para abrir a lista de conectores disponíveis.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/JIdUrJEU8uxjjZo4faRf.png" align="center"></figure>
    
3.  Na lista, escolha **Conector SNMP**
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/UtNiKc0mpDeOn0hSiTUr.png" align="center"></figure>
    
    <br />
    

Uma vez selecionado, a janela de configuração do Conector SNMP é exibida.

<br />

**Parâmetros de Configuração do Conector**

-   **Tipo de Frequência**<br />
    Define a frequência com que o pipeline será executado:
    
    -   **Periódico**:<br />
        O pipeline é executado pela primeira vez após o número de segundos definidos no _Tempo de Atualização (segs)_ a partir do momento em que o plugin for instalado.<br />
        Após cada execução, o pipeline espera o mesmo intervalo antes de ser executado novamente.
    -   **Agendado**:<br />
        A execução do pipeline é configurada usando uma **expressão cron**, semelhante a um crontab. Isso permite o agendamento preciso por minutos, horas, dias, semanas ou meses.
-   **Tempo de Atualização (segs)** _(Somente Periódico)_<br />
    Intervalo, em segundos, entre cada execução do pipeline.
-   **Número de Execuções**
    
    -   `-1`: O pipeline será executado indefinidamente.
    -   Qualquer número positivo: O pipeline será executado exatamente esse número de vezes.
-   **Sessão**<br />
    Um parâmetro obrigatório usado internamente pelo módulo para gerenciar a execução.<br />
    Deve ser um **valor em string** e identificar a sessão de forma exclusiva.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/t5FcSc6KWYd8IxgYYNUl.png"></figure>

<br />

-   **hostPartitionSize** _(padrão 0)_<br />
    Define o número máximo de hosts a serem agrupados e consultados em cada lote.
-   **partitionDelay (secs)** _(padrão 30)_<br />
    Define o número de segundos a serem aguardados entre a execução de cada lote.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/4BG6bduRzTbAq96dfPRy.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/iSV5XZ1rRAuRtGnkSwXz.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/Z8iIEKxtBX6hVKCNMVbl.png" align="center"></figure>

**Como o Particionamento de Host Funciona**

Ao consultar um grande número de hosts, o **hostPartitionSize** e o **partitionDelay** permitem que a carga de trabalho seja dividida em lotes gerenciáveis.

Por exemplo:

-   Se `hostPartitionSize = 20` e `partitionDelay = 10`, e o pipeline tiver 100 dispositivos:
    
    -   O sistema dividirá os 100 hosts em 5 grupos de 20.
    -   Cada grupo de 20 será consultado sequencialmente, aguardando 10 segundos entre os grupos.

Exemplo de cronograma de execução:

-   Consultar 20 hosts → 00:00:00 – 00:00:05
-   Aguardar 10 segundos
-   Consultar os próximos 20 hosts → 00:00:15 – 00:00:20
-   Aguardar 10 segundos
-   Consultar os próximos 20 hosts → 00:00:30 – 00:00:35
-   Aguardar 10 segundos
-   Consultar os próximos 20 hosts → 00:00:45 – 00:00:50
-   Aguardar 10 segundos
-   Consultar os últimos 20 hosts → 00:01:05

Ao final do ciclo, o pipeline aguarda até a próxima execução agendada.

⚠️ **Nota Importante:** Se o tempo total de consulta (incluindo os atrasos) exceder o intervalo definido na expressão cron ou no tempo de atualização, as execuções poderão **sobrepor-se**. Isso pode gerar timestamps incorretos nos dados coletados. Sempre valide se o tamanho das partições e os atrasos estão devidamente alinhados com a programação do pipeline.

<br />

**Credenciais Padrão**

O Conector SNMP também requer **credenciais padrão**:

-   **Versão SNMP** (ex., 2c, 3).
-   **Comunidade** (para SNMP v1/v2c).
-   **Campos de autenticação e privacidade** (para SNMP v3).

Essas credenciais são aplicadas por padrão a todos os hosts, no entanto, podem ser substituídas de forma individual ao adicionar hosts ao conector.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/DYTdXdo5eEivi7p3oheO.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/VTjDadscYiuwjKBqdoYS.png" align="center"></figure>

<div class="sd-callout" data-callout-type="info">A <strong>seção de Hosts</strong> é normalmente provisionada por meio do <strong>Módulo de Inventário</strong>, que possibilita um provisionamento massivo e organizado dos dispositivos. Esse método é recomendado ao se gerenciar um grande número de hosts, garantindo consistência e eficiência.</div>

<div class="sd-callout" data-callout-type="info">Contudo, também é possível adicionar os hosts de forma manual e individual usando o botão <strong>Adicionar Host</strong>, especificando para cada dispositivo o seu respectivo <strong>Grupo de OID</strong>.</div>

<br />

**Resumo**

O Conector SNMP no estágio Extract possibilita uma pesquisa flexível e escalonável de dispositivos de rede:

-   Modos de execução **Periódico** ou **Agendado**.
-   Execução contínua com `-1` ou execuções limitadas mediante um número fixo.
-   O parâmetro Sessão é obrigatório.
-   O particionamento (hostPartitionSize, partitionDelay) previne sobrecargas e melhora a eficiência.
-   Requer a presença de no mínimo um host e credenciais SNMP válidas.

Sua configuração correta assegura uma extração de dados otimizada e confiável para os estágios posteriores de transformação e carga.

<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />