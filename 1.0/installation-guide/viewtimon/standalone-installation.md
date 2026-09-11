---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Standalone Installation'
id: 3QS-ZQO7-DIX-JDN
slug: standalone-installation
isVisible: true
lastUpdated: '2025-07-17 11:25:11'
---
# **<span align="center">Instalando o Módulo Viewtimon</span>**

> ⚠️ **Pré-requisitos e Avisos Legais**
> 
> -   O recurso **Viewtimon** deve estar licenciado e visível em **Viewtimon** na barra lateral.
> -   **Alta Disponibilidade (HA) não é suportada** para o Viewtimon nesta versão. Você só pode implantar uma instância de nó único.

---

### **Iniciando o Instalador**

1.  Faça login no **Viewtimanager** como um administrador ou um usuário com privilégios de instalação.
2.  Na navegação à esquerda, clique em **Viewtimon**.
3.  Clique no botão **INSTALL VIEWTIMON** (Instalar Viewtimon).}
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/OT95DV0aQBm6aF7KZOch.png" align="center"></figure>
    

### **Definindo o Host do Cluster**

> Como o HA não é suportado, você configurará apenas um único nó.

1.  Em **Cluster for Viewtimon**, clique em **\+ ADD NEW HOST** (Adicionar Novo Host).
    
    <br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/K8cnKPmbJnkcb19G4bH0.png">
    
    <br />
    
2.  Na linha da **Cluster Host List** (Lista de Hosts do Cluster), insira:
    
    -   **Hostname or IP Address (Nome de Host ou Endereço IP)**: o IP de gerenciamento do seu servidor Viewtimon (ex: `10.30.23.4`).
    -   **LAN Hostname or IP Address (Nome de Host da LAN ou Endereço IP)**: o mesmo valor acima.
    -   **Password (Senha)** e **Password confirm (Confirmar Senha)**: a senha SSH para o usuário `viewtinet` naquele host.
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/oKm9TleIgcASvcXdKDR1.png">
    
    <br />
    
3.  Clique em **SAVE CHANGES** (Salvar Alterações) e confirme a caixa de diálogo:
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/V7zJCYgoIwlSHtp95y6c.png" align="center"></figure>
    

<br />

### **Executando o Instalador**

1.  Assim que o host for aceito, o log de instalação será transmitido no painel.
2.  Aguarde até ver **“Installation finished”** (Instalação concluída) e nenhum erro fatal.
3.  Clique em **FINISH INSTALLATION** (Concluir Instalação) para finalizar.
    
    <br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/DGdvQs9RTorsIrbsAAgz.png">
    

---

### **Atribuindo Interfaces de Tráfego**

1.  Navegue até **Networking → INTERFACES**.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/pQoATLuNFRwYgIf1NUR6.png" align="center"></figure>
    
2.  Localize as NICs que você deseja dedicar ao Viewtimon.
3.  Marque a caixa do **Viewtimon** para cada interface ( **não** ative o HA).
4.  Clique em **SAVE CHANGES** (Salvar Alterações) e confirme o banner vermelho:
    
    > “Please restart Viewtimon to apply config changes” (Reinicie o Viewtimon para aplicar as alterações de configuração)
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/AgESE5h1xa4wtmDeZUFE.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/1k2LWlMSnyGo4h4k5VY4.png" align="center"></figure>

### **Iniciando o Serviço**

1.  Retorne para **Viewtimon → STATUS**.
2.  Clique em **START** (Iniciar).
    
    <br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/VsvsBv7XhHJQGfGnwsZU.png">
    
    <br />
    
3.  Confirme o prompt **“Do you want to start this module?”** (Deseja iniciar este módulo?) clicando em **YES** (Sim).
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/HGyEMTPrv0ljWju9ScMk.png" align="center"></figure>
    
4.  O indicador de status do Viewtimon ficará verde e gráficos de desempenho aparecerão.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/7MSwma8VHOuuETm2ysB6.png" align="center"></figure>

🎉 **O Viewtimon agora está instalado e em execução.** Você pode monitorar o tráfego em tempo real