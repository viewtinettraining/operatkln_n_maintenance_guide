---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Cluster Installation'
id: NQU-2BQB-PAX-CE8
slug: cluster-installation
isVisible: true
lastUpdated: '2025-10-15 10:16:28'
---
# **<span align="center">Instalação em Modo Cluster para o Viewtisight</span>**

<br />

<span align="justify">Por padrão, os módulos de interface gráfica do usuário Viewtisight, Viewtimanager e Viewtiaut, juntamente com o módulo Viewticore, são instalados juntos em uma implantação "Autônoma" (Standalone). Consequentemente, não há um capítulo de instalação separado para esses componentes. No entanto, quando você precisa de uma configuração em cluster de alta disponibilidade com dois ou mais nós, deve adicionar e configurar cada servidor adicional. Este capítulo detalha as etapas para implantar um segundo nó do Viewtisight.</span>

<br />

## **Pré-requisitos**<br />

### **Requisitos Obrigatórios**

-   **Nó primário instalado e licenciado**: O primeiro nó do cluster deve estar totalmente instalado e operacional por meio do processo de instalação do pacote (bundle).
-   **Tamanho do cluster**: Pelo menos **2 nós**—um designado como **master** (mestre), e o outro como seu **mirror** (espelho).
-   **VIP flutuante**: Um endereço IPv4 dedicado para failover.
-   Certifique-se de que os relógios do sistema em todos os nós do cluster estejam sincronizados; a integração com um serviço NTP é obrigatória

<br />

### **Recomendado para Desempenho Ideal**

-   **Hardware homogêneo**: CPU, RAM e armazenamento idênticos em todos os nós do cluster.
-   **Rede inter-nós separada**: Uma placa de rede (NIC) adicional em cada servidor para heartbeat e sincronização, usando seu próprio IP Virtual.
    
    <br />
    

### **Visão Geral da Rede**

Abaixo está uma visão de alto nível de um cluster Viewtisight de alta disponibilidade com dois nós:

-   **Acesso do cliente**: Todo o tráfego (HTTP/HTTPS) vai para o VIP flutuante **10.30.23.21**, gerenciado pelo Keepalived.
-   **Nó mestre**: O **Nó 1** (eth0: 10.30.23.5) recebe o tráfego por padrão.
-   **Nó de failover**: O **Nó 2** (eth0: 10.30.23.6) assume se o Nó 1 falhar.
-   **Heartbeat e sincronização**: Um link dedicado entre **10.100.100.100** (Nó 1 eth1) e **10.100.100.101** (Nó 2 eth1) transporta o estado do cluster e as verificações de integridade.
-   **Configuração adicional** Para permitir a comunicação inter-nós, você deve configurar as NICs adicionais via Netplan—edite os arquivos YAML em `/etc/netplan/` para atribuir os endereços estáticos 10.100.100.x.
    
    <br />
    
    <div class="sd-callout" data-callout-type="warning">Os nomes das interfaces (ex: <code>eth1</code>) podem variar dependendo do seu sistema operacional e convenções de nomenclatura; ajuste adequadamente.</div>
    

<span align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/st3TBf1ZPapYO8coCI5t.png"></span>

### **<br />
Configuração de Portas**

<span align="justify">Se os nós do seu cluster Viewtinet estiverem espalhados em datacenters geograficamente separados, residirem em sub-redes diferentes ou ficarem atrás de firewalls ou gateways VPN, você deverá abrir explicitamente todas as portas de serviço e do HA-Proxy necessárias em todos os dispositivos de segurança (regras de firewall, ACLs de roteador, grupos de segurança em nuvem, etc.). Isso inclui portas de réplica do MongoDB (23450, 23459), portas HTTP/HTTPS de backend/frontend (4500–4605), portas do Viewticore e Dhyana (8091, 9988, 9095) e portas do ouvinte do HA-Proxy (4000–5001, 8080, 443). Se qualquer uma dessas portas permanecer bloqueada, a sincronização inter-nós, as verificações de integridade e o acesso do usuário às interfaces de gerenciamento falharão, e o cluster HA não funcionará.<br></span>

Abaixo está a lista de portas de serviço publicadas por cada componente e as portas de front-end do HA-Proxy para uma configuração HA de dois nós:

<br />

<table><tbody><tr><th><p><span align="center">Componente</span></p></th><th><p><span align="center">Porta de Serviço</span></p></th><th><p><span align="center">Porta HA-Proxy</span></p></th></tr><tr><td><p><span align="center">Viewtiauth-mongo</span></p></td><td><p><span align="center">23450</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtiauth-mongo-arbiter</span></p></td><td><p><span align="center">8540</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtiauth-backend-HTTP</span></p></td><td><p><span align="center">4500</span></p></td><td><p><span align="center">4000</span></p></td></tr><tr><td><p><span align="center">Viewtiauth-frontend-HTTP</span></p></td><td><p><span align="center">4600</span></p></td><td><p><span align="center">4200</span></p></td></tr><tr><td><p><span align="center">Viewtiauth-backend-HTTPS</span></p></td><td><p><span align="center">4501</span></p></td><td><p><span align="center">4001</span></p></td></tr><tr><td><p><span align="center">Viewtiauth-frontend-HTTPS</span></p></td><td><p><span align="center">4601</span></p></td><td><p><span align="center">4201</span></p></td></tr><tr><td><p><span align="center">Viewtisight-mongo</span></p></td><td><p><span align="center">23459</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtisight-mongo-arbiter</span></p></td><td><p><span align="center">8451</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtisight-backend-HTTP</span></p></td><td><p><span align="center">4502</span></p></td><td><p><span align="center">4101</span></p></td></tr><tr><td><p><span align="center">Viewtisight-frontend-HTTP</span></p></td><td><p><span align="center">4602</span></p></td><td><p><span align="center">8080</span></p></td></tr><tr><td><p><span align="center">Viewtisight-backend-HTTPS</span></p></td><td><p><span align="center">4503</span></p></td><td><p><span align="center">4102</span></p></td></tr><tr><td><p><span align="center">Viewtisight-frontend-HTTPS</span></p></td><td><p><span align="center">4603</span></p></td><td><p><span align="center">443</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-mongo</span></p></td><td><p><span align="center">23451</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-mongo-arbiter</span></p></td><td><p><span align="center">8452</span></p></td><td><p><span align="center">N/A</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-backend-HTTP</span></p></td><td><p><span align="center">4504</span></p></td><td><p><span align="center">1337</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-frontend-HTTP</span></p></td><td><p><span align="center">4604</span></p></td><td><p><span align="center">5000</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-backend-HTTPS</span></p></td><td><p><span align="center">4505</span></p></td><td><p><span align="center">1339</span></p></td></tr><tr><td><p><span align="center">Viewtimanager-frontend-HTTPS</span></p></td><td><p><span align="center">4605</span></p></td><td><p><span align="center">5001</span></p></td></tr><tr><td><p><span align="center">Viewticore-gateway</span></p></td><td><p><span align="center">8091</span></p></td><td><p><span align="center">8090</span></p></td></tr><tr><td><p><span align="center">Viewticore-alarms</span></p></td><td><p><span align="center">9988</span></p></td><td><p><span align="center">9987</span></p></td></tr><tr><td><p><span align="center">Dhyana</span></p></td><td><p><span align="center">9095</span></p></td><td><p><span align="center">N/A</span></p></td></tr></tbody></table>

<br />

---

<br />

## **Adicionando um Segundo Nó via Viewtimanager**

<br />

Siga estas etapas para implantar o segundo nó para os módulos **Viewtisight**, **Viewtimanager** e **Viewtiauth** a partir do nó mestre:

-   **Faça login no Viewtimanager (Master)**
    
    -   Abra seu navegador e acesse<br />
        `http://MASTER-NODE-IP:4200/`
    -   Autentique-se com as credenciais do administrador e escolha o Viewtimanager.<br />
        
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/d1evQxpHA2lOK9OUbj8g.png"></figure>
    
    <br />
    
    <figure align="center" style="width:51%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/3vTRuPMSbOvFkCQZI9v4.png" width="51%" align="center"></figure>
    
    <br />
    
-   **Navegue até a Aba Viewtisight Hosts**
    
    -   No menu à esquerda, clique em **Viewtisight**.<br />
        
    
    <figure align="center" style="width:46%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/Pv2ipyiPw87a79CYZoZd.png" width="46%" align="center"></figure>
    
    -   Selecione a aba **Hosts** no topo da página.
        
        <br />
        
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/ObLdrCbd5ZrP449RxiPn.png" align="center"></figure>
    

### **Adicionar o Segundo Nó ao Viewtisight**

-   Clique em **Add New Host** (Adicionar Novo Host):

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/ExoBlLBZcstkvswwMLdh.png" align="center"></figure>

-   Se a configuração do Nó 1 usar o mesmo endereço IP para o "Nome de Host ou Endereço IP" e o "Nome de Host da LAN ou Endereço IP", você deve atualizar o IP da rede de comunicação inter-nós para corresponder à rede dedicada definida para esse fim.
-   **Hostname or IP Address (Nome de Host ou Endereço IP)**: Especifique o nome de domínio totalmente qualificado (FQDN) ou o IP da interface de gerenciamento do Nó 2 (por exemplo, `10.30.23.6`).
-   **LAN Hostname or IP Address (Nome de Host da LAN ou Endereço IP)** : Especifique o nome de domínio totalmente qualificado (FQDN) ou o IP da interface de comunicação inter-nós do Nó 2 (por exemplo, `10.100.100.2`).
-   **Password & Password confirm (Senha e Confirmar senha)**: Forneça as mesmas credenciais SSH usadas para o Nó 2

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/xkQUZT64sXfBCFC9uEbl.png" align="center"></figure>

<br />

-   Clique em **ADD NEW VIRTUAL ADDRESS** (Adicionar Novo Endereço Virtual):
-   **Virtual IP Address (Endereço IP Virtual):** Especifique o nome de domínio totalmente qualificado (FQDN) ou o endereço IP Virtual (VIP) (ex: 10.30.23.21).
-   Clique em **Save** (Salvar).
-   Confirme as alterações

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/G7cbEmXoE5flk5NrPG4O.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/Oo1WRrTZCzMUDah9c1ys.png" align="center"></figure>

-   Aguarde até que o indicador de status do novo host mude para **Online** ou **Healthy** (Saudável).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/yxcTikUbOCehS7nD7JmY.png" align="center"></figure>

<br />

-   <span align="justify">Como cada servidor requer sua própria licença no modelo da Viewtinet, você deve obter o </span> arquivo `server-info.txt` conforme descrito na seção "Obtendo Informações do Servidor" ("Getting Server Info") do capítulo "Instalação do Pacote" ("Bundle Installation").
-   <span align="justify">Assim que você receber o arquivo de licença do seu representante da Viewtinet, execute as etapas "Ativação do Usuário Administrador" ("Admin User Activation") e "Carregar Licença" ("Upload License") no segundo nó do cluster, conforme descrito nas seções correspondentes do capítulo "Instalação do Pacote" ("Bundle Installation").</span>
    
    <br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/hyRlkoqouQjbs3txAQHT.png"></figure>
    
    <br />
    

<br />