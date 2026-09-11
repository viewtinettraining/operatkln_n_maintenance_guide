---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Standalone Installation'
id: 2DJ-N7C3-94R-9K7
slug: standalone-installation
isVisible: true
lastUpdated: '2025-10-15 10:34:00'
---
# **<span align="center">Instalando o Módulo Viewtify QoS</span>**

<br />

> ⚠️ **Pré-requisitos e Avisos Legais**
> 
> -   O recurso **Viewtify QoS** deve estar licenciado e visível em **Viewtify QoS** na barra lateral.
> -   O **Viewtimon** já deve estar instalado e em execução.
> -   **Alta Disponibilidade (HA) não é suportada** para o Viewtify QoS nesta versão. Você só pode implantar uma instância de nó único.

---

## **Iniciar o Instalador do QoS**

1.  Na interface de usuário do Viewtimanager, clique em **Viewtify QoS** na navegação à esquerda.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/ZhLfy030UTajqcjupsaf.png" align="center"></figure>
    
2.  Clique no botão **INSTALL QOS** (Instalar QoS).
    
    <br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/3pW2VhIXRaNx1p0HIhrc.png">
    

---

<br />

## **Adicionar o Host do Cluster**

1.  Em **Cluster for QoS**, clique em **\+ ADD NEW HOST** (Adicionar Novo Host).
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/PQO6d4eeYqFfpdTRaKQV.png" align="center"></figure>
    
2.  Na nova linha, insira:
    
    -   **Hostname or IP Address (Nome de Host ou Endereço IP)**: IP de gerenciamento (ex: `10.30.23.4`).
    -   **LAN Hostname or IP Address (Nome de Host da LAN ou Endereço IP)**: o mesmo valor acima.
    -   **Password (Senha)** / **Password confirm (Confirmar Senha)**: senha SSH do usuário `viewtinet` naquele host.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/fyX8Urcv3SJu3QcnLQrA.png" align="center"></figure>
    
3.  Clique em **SAVE CHANGES** (Salvar Alterações) e confirme:
    
    > “This module will be active in: 10.30.23.4” → **OK**
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/47LgIjH70AQypet9xYTy.png" align="center"></figure>

## **Concluir a Instalação**

1.  Aguarde até que o log do instalador seja transmitido e relate **“Installation finished”** (Instalação concluída).
2.  Clique em **FINISH INSTALLATION** (Concluir Instalação).
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/gXfRvqikCkDex5c4vzJG.png" align="center"></figure>
    

### **Parar o Viewtimon Antes da Ligação (Binding) de Interfaces**

> ### O Viewtify QoS requer vinculação exclusiva de placas de rede (NICs), então você deve primeiro parar o serviço do Viewtimon.

1.  Navegue até **Viewtimon → STATUS**.
2.  Clique em **STOP** (Parar) e confirme **“Do you want to stop this module?”** (Deseja parar este módulo?) → **YES** (Sim).
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/J7aP4l3GWIz59zG6rf4H.png" align="center"></figure>
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/d6aDAJXV83rAIQrInAXN.png" align="center"></figure>

### **Atribuir Interfaces para o QoS**

1.  Vá para **Networking → INTERFACES**.
2.  Para cada NIC de sonda (probe) que você deseja usar com o QoS, marque a caixa **Viewtify QoS**.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/zNd62gHxWkr4LSP3EheD.png" align="center"></figure>
    
3.  Clique em **SAVE CHANGES** (Salvar Alterações).
4.  Confirme o banner vermelho: **“Please restart Viewtimon to apply config changes”** (Reinicie o Viewtimon para aplicar as alterações de configuração).
    
    <br />
    

---

### **Reiniciar o Viewtimon**

> ### Reiniciar o Viewtimon carregará as novas vinculações de QoS.

1.  Retorne para **Viewtimon → STATUS**.
2.  Clique em **RESTART** (Reiniciar) (ou **START**, se ainda estiver parado).
3.  Confirme **“Do you want to start this module?”** (Deseja iniciar este módulo?) → **YES** (Sim).
4.  O indicador do Viewtimon ficará verde e as luzes de status do **Viewtimon** e do **Viewtify QoS** ficarão ativas.

---

🎉 **O Viewtify QoS agora está instalado e em execução.**<br />
Você pode começar a criar políticas de modelagem de tráfego e priorização.