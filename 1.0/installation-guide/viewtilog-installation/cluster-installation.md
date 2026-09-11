---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Instalação em Cluster'
id: ND7-Z3HP-QAV-NIZ
slug: cluster-installation
isVisible: true
lastUpdated: '2025-10-15 10:22:27'
---
# **<span align="center">Instalação em Modo Cluster para o Viewtilog</span>**

<br />

<span align="justify">Quando implantado no modo de Alta Disponibilidade (H.A.), o Viewtilog opera como um cluster de dois ou mais nós que coletam e replicam continuamente dados de monitoramento e de log. Isso abrange métricas de desempenho de rede via SNMP, registros NetFlow, mensagens syslog, registros de detalhes de chamadas (CDRs) e quaisquer outras fontes habilitadas. Um VIP flutuante gerenciado pelo Keepalived e balanceado pelo HAProxy garante ingestão ininterrupta: se um nó falhar, o tráfego muda automaticamente para o backup, enquanto em condições normais a carga é distribuída uniformemente. Configurações avançadas de cluster e balanceamento de carga estão documentadas no Guia do Usuário do Viewtilog.</span>

<br />

## **Pré-requisitos**<br />

### **Requisitos Obrigatórios**

-   **Nó primário com o Viewtilog instalado e licenciado**: O primeiro nó do cluster deve ter o Viewtilog totalmente instalado, licenciado (incluindo o recurso H.A.) e operacional por meio do processo de instalação do pacote (bundle).
-   **Tamanho do cluster**: Pelo menos **2 nós**—um designado como **master** (mestre), e o outro como seu **mirror** (espelho).
-   **VIP flutuante**: Um endereço IPv4 dedicado para failover.
-   Certifique-se de que os relógios do sistema em todos os nós do cluster estejam sincronizados; a integração com um serviço NTP é obrigatória

### **Recomendado para Desempenho Ideal**

-   **Hardware homogêneo**: CPU, RAM e armazenamento idênticos em todos os nós do cluster.
-   **Rede inter-nós separada**: Uma placa de rede (NIC) adicional em cada servidor para heartbeat e sincronização, usando seu próprio IP Virtual.

### **Requisitos Opcionais**

-   **Sub-rede de serviço dedicada**: Use uma rede separada (ex: 10.100.x.x/24) para todo o tráfego de coleta de logs e métricas.
-   **Interfaces de rede adicionais**: Configure NICs adicionais em cada nó usando endereços IP fora da rede de gerenciamento para isolar o tráfego de coleta de logs e métricas.
-   **VLAN separada**: Coloque o tráfego de serviço e sincronização em uma VLAN dedicada para aprimorar a segurança e o desempenho.

<br />

### **Visão Geral da Rede**

Neste cluster Viewtilog de Alta Disponibilidade, as métricas de SNMP, ICMP e baseadas em API são ativamente consultadas pelos nós do Viewtilog, enquanto o tráfego de syslog e NetFlow é enviado das fontes de dados para o VIP flutuante (10.30.23.21). O VIP direciona os dados de log e fluxo de entrada para a interface de gerenciamento do nó ativo: normalmente **Nó 1** (eth0: 10.30.23.5), com failover automático para o **Nó 2** (eth0: 10.30.23.6) se o primário cair. Um link inter-nós dedicado (eth1) em 10.100.100.100 ↔ 10.100.100.101 carrega o heartbeat, a sincronização de estado e o tráfego de replicação para manter o cluster coordenado.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/GqV7J5L0AXdNhO4L2t1T.png"></figure>

<br />

<div class="sd-callout" data-callout-type="warning">Os nomes das interfaces (ex: <code>eth1</code>) podem variar dependendo do seu sistema operacional e convenções de nomenclatura; ajuste adequadamente.<br></div>

<br />

## **Adicionando um Segundo Nó Viewtilog via Viewtimanager**

<br />

Siga estas etapas para implantar o segundo nó para os módulos **Viewtisight**, **Viewtimanager** e **Viewtiauth** a partir do nó mestre:

-   **Faça login no Viewtimanager (VIP)**
    
    -   Abra seu navegador e acesse<br />
        `http://VIP-IP:4200/`
    -   Autentique-se com as credenciais do administrador e escolha o Viewtimanager.

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/d1evQxpHA2lOK9OUbj8g.png"><br />
<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/3vTRuPMSbOvFkCQZI9v4.png" align="center"></figure>

-   **Navegue até a Aba Viewtilog Hosts**
    
    -   No menu à esquerda, clique em **Viewtilog**.<br />
        

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/kg9NJU6ccpYUp0wo5qsK.png" align="center"></figure>

-   Selecione a aba **Hosts** no topo da página.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/ATD3VSzFNjQj9Pu9vPbs.png" align="center"></figure>

## **Adicionar o Segundo Nó ao Viewtilog**

-   Clique em **Add New Host** (Adicionar Novo Host):

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/cytJw3BFf6ltd2sozuMW.png"></figure>

-   <span align="justify">Se a configuração do Nó 1 usar o mesmo endereço IP para o "Nome de Host ou Endereço IP" e o "Nome de Host da LAN ou Endereço IP", você deve atualizar o IP da rede de comunicação inter-nós para corresponder à rede dedicada definida para esse fim.</span>
-   **Hostname or IP Address (Nome de Host ou Endereço IP)**: Especifique o nome de domínio totalmente qualificado (FQDN) ou o IP da interface de gerenciamento do Nó 2 (por exemplo, `10.30.23.6`).
-   **LAN Hostname or IP Address (Nome de Host da LAN ou Endereço IP)** : Especifique o nome de domínio totalmente qualificado (FQDN) ou o IP da interface de comunicação inter-nós do Nó 2 (por exemplo, `10.100.100.2`).
-   **Password & Password confirm (Senha e Confirmar senha)**: Forneça as mesmas credenciais SSH usadas para o Nó 2

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/lQ3ePdpGdoRij5qQuZSw.png"></figure>

-   Clique em **ADD NEW VIRTUAL ADDRESS** (Adicionar Novo Endereço Virtual):
-   **Virtual IP Address (Endereço IP Virtual):** Especifique o nome de domínio totalmente qualificado (FQDN) ou o endereço IP Virtual (VIP) (ex: 10.30.23.21).
-   Clique em **Save** (Salvar).
-   Confirme as alterações

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/WmbAR5g2dFrKqp5U2ULP.png"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/opuAOZSDeSq7YxumkKNx.png" align="center"></figure>

-   Aguarde até que a mensagem 'Installation Finished' (Instalação Concluída) apareça.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/2wb3s63FPruz26GV6hQO.png"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/z06h397milw76pSOBr9x.png"></figure>

<br />