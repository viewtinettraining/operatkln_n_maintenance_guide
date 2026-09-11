---
reusableId: 105
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Instalação Standalone'
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
> -   **Alta Disponibilidade (HA) não é suportada** para o Viewtify QoS nesta versão. Só é possível implantar uma instância de nó único.

---

## **Iniciar o Instalador do QoS**

1.  Na interface do Viewtimanager, clique em **Viewtify QoS** na navegação à esquerda.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/ZhLfy030UTajqcjupsaf.png" align="center"></figure>
    
2.  Clique no botão **INSTALAR QOS**.
    
    <br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/3pW2VhIXRaNx1p0HIhrc.png">
    

---

<br />

## **Adicionar o Host ao Cluster**

1.  Em **Cluster para QoS**, clique em **\+ ADICIONAR NOVO HOST**.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/PQO6d4eeYqFfpdTRaKQV.png" align="center"></figure>
    
2.  Na nova linha, insira:
    
    -   **Hostname ou Endereço IP**: IP de gerência (ex.: `10.30.23.4`).
    -   **Hostname ou Endereço IP LAN**: mesmo que acima.
    -   **Senha** / **Confirmar senha**: senha SSH do usuário `viewtinet` naquele host.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/fyX8Urcv3SJu3QcnLQrA.png" align="center"></figure>
    
3.  Clique em **SALVAR ALTERAÇÕES** e confirme:
    
    > “Este módulo ficará ativo em: 10.30.23.4” → **OK**
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/47LgIjH70AQypet9xYTy.png" align="center"></figure>

## **Concluir a Instalação**

1.  Aguarde o log do instalador transmitir e relatar **“Instalação concluída”**.
2.  Clique em **FINALIZAR INSTALAÇÃO**.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/gXfRvqikCkDex5c4vzJG.png" align="center"></figure>
    

### **Parar o Viewtimon Antes de Vincular Interfaces**

> ### O Viewtify QoS requer vinculação exclusiva das NICs; portanto, você deve primeiro parar o serviço Viewtimon.

1.  Navegue até **Viewtimon → STATUS**.
2.  Clique em **PARAR** e confirme **“Deseja parar este módulo?” → SIM**.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/J7aP4l3GWIz59zG6rf4H.png" align="center"></figure>
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/d6aDAJXV83rAIQrInAXN.png" align="center"></figure>

### **Atribuir Interfaces para QoS**

1.  Vá para **Rede → INTERFACES**.
2.  Para cada NIC de sonda que deseja usar com QoS, marque a caixa **Viewtify QoS**.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/zNd62gHxWkr4LSP3EheD.png" align="center"></figure>
    
3.  Clique em **SALVAR ALTERAÇÕES**.
4.  Confirme o banner vermelho: **“Reinicie o Viewtimon para aplicar as alterações de configuração”**.
    
    <br />
    

---

### **Reiniciar o Viewtimon**

> ### Reiniciar o Viewtimon carregará as novas vinculações de QoS.

1.  Retorne a **Viewtimon → STATUS**.
2.  Clique em **REINICIAR** (ou **INICIAR**, se ainda estiver parado).
3.  Confirme **“Deseja iniciar este módulo?” → SIM**.
4.  O indicador do Viewtimon ficará verde e os indicadores de status do **Viewtimon** e do **Viewtify QoS** ficarão ativos.

---

🎉 **O Viewtify QoS está agora instalado e em execução.**<br />
Você pode começar a criar políticas de moldagem de tráfego e priorização
