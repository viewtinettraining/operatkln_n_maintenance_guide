---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Introdução'
slug: intro
isVisible: true
isSearchable: true
id: H4I-A1D-ZM6-Q3O
---
# **<span align="center">Networking</span>**

<br />

Esta seção cobre as configurações de rede para os módulos **Viewtimon** e **Viewtify QoS**. É importante notar que esta configuração **não tem nada a ver** com a configuração de rede de gerenciamento do dispositivo ou com a rede de serviço usada para coleta de logs, métricas, SNMP, Netflow e APIs pelo módulo Viewtilog.

<br />

---

## **Management & Service Planes in DPI Solutions**

No contexto de soluções DPI (Deep Packet Inspection), planos de gerenciamento (**management**) e serviço (**service planes**) referem-se às camadas funcionais distintas que lidam com diferentes aspectos das operações de rede:

- **Management Plane:** Este plano é responsável pela configuração, monitoramento e administração da solução DPI. Ele inclui funcionalidades como aplicação de políticas, autenticação de usuários, log do sistema e monitoramento de desempenho.
- **Service Plane (Wire Data):** Este plano foca no processamento e análise do tráfego de rede. Ele lida com tarefas como inspeção de pacotes, classificação de tráfego, aplicação de QoS e aplicação de políticas de segurança.

Esses planos trabalham juntos para garantir a análise eficiente do tráfego de rede, a aplicação de políticas e a confiabilidade geral do sistema.

<br />

---

## **Interface and IP Address Combinations for Viewtimon**

O Viewtimon trabalha com uma cópia do tráfego, que pode ser fornecida através de port-mirroring, usando um TAP, ou com port span. Neste caso, cada interface captura o tráfego de rede sem interferir no seu fluxo.

- **No interface pairing is required**, o que significa que, se houver **M interfaces, todas poderão ser usadas simultaneamente (Service Plane)**.
- **IP addresses are assigned only to management interfaces (Management Plane)**.

<br />

### **Viewtimon Deployment**

A Viewtinet precisa receber uma cópia do tráfego IP para observabilidade dos Wire Data. Conforme ilustrado abaixo, isso pode ser feito com um TAP, port span ou packet broker.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-intro-3.png" align="center"></figure>

<br />

---

## **Interface and IP Address Combinations for Viewtify QoS**

- O Viewtify QoS opera no modo ponte (**bridge mode**) na Camada 2 do modelo OSI.
- A implantação no **Bridge mode** normalmente requer **pares de interfaces** para atuar como uma ponte transparente.
- Se houver **N interfaces físicas**, elas podem ser agrupadas em pares para formar **N/2 Bridge links**.
- Como o tráfego passa por lá sem modificar IPs, as interfaces em modo Bridge **geralmente não têm endereços IP atribuídos (Service Plane)**, exceto por uma interface de gerenciamento dedicada **(Management Plane)**.

<br />

### **Viewtify Deployment**

Para Controle de Tráfego, o Viewtinet precisa ser implantado em linha (inline) com um bypass passivo.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-intro-5.png" align="center"></figure>

<br />

---

## **The Viewtinet Bypass Device**

O bypass é um dispositivo obrigatório ao implantar o Viewtify QoS inline. O **Bypasser** é um processo de watchdog para o Classificador (The Probe).

- O processo Bypasser envia batimentos cardíacos (heartbeats) periódicos ao dispositivo de Bypass da Viewtinet para indicar que o Classificador está ativo e funcionando normalmente.
- O envio de heartbeats coloca/mantém o dispositivo de Bypass em um estado ativo (**Active State**), para que o tráfego de rede seja direcionado através do Servidor do Appliance (The Probe).
- Se o processo Bypasser parar de enviar heartbeats (indicando falha), o dispositivo de Bypass muda internamente para o estado de bypass (**Bypass State**), de modo que o tráfego de rede é contornado (bypassed) diretamente entre a LAN e a Internet, não enviando o tráfego através do servidor do Appliance.

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-1.png" align="center">
  <figcaption><b>Picture 1: The Bypasser's role in the big picture.</b></figcaption>
</figure>

<br />

### **Heartbeats and Operations**

- Os heartbeats são enviados a cada 100 ms pelo processo Bypasser ao dispositivo de Bypass para indicar que está tudo OK.
- Se o processo Bypasser detectar um erro, nenhum heartbeat será enviado.
- O processo Bypasser é usado como Watchdog para o The Probe. Opcionalmente, extensões podem ser usadas como Watchdogs para outros serviços, como Viewtify OPT.
- O processo Bypasser também gerencia os Heartbeats, a detecção USB e atua como servidor de configuração, controlado pelo ViewtiManager.
- O processo monitorado (The Probe) é um "processo inteligente com watchdog", que indica se está "operacional" ou não através de notificações Push (Push Notifications). Neste caso, "operacional" significa que o The Probe está em execução e pode processar tráfego de rede de entrada.
- O processo Bypasser assina as notificações Push para detectar quaisquer "mudanças operacionais" no The Probe.
- O ViewtiManager pode controlar o processo Bypasser através de sua GUI baseada na web.
- Toda a comunicação entre o processo Bypasser e o dispositivo de Bypass ocorre através de um cabo USB. O dispositivo de Bypass também usa USB como sua fonte de alimentação. Sem energia, o dispositivo de Bypass muda para o Bypass State automaticamente.

### **Failure Detection**

Se o dispositivo de Bypass da Viewtinet não receber um heartbeat dentro de um período de tempo limite (configurável), isso é considerado uma falha, e o dispositivo muda para o estado de Bypass (Bypass State). As falhas são definidas como:

- Falha no classificador (relatando NOT_READY, processo morreu, não está respondendo ao Bypasser, etc.)
- Falha no Bypasser (processo morreu, etc.)
- Falha no servidor (desligado, kernel panic, etc.)
- Cabo USB desconectado (isso desliga o dispositivo de Bypass da Viewtinet)

### **Active State & Bypass State**

- Sem nenhuma falha, o dispositivo de Bypass da Viewtinet deve enviar todo o tráfego para o Classificador e é dito estar em um estado ativo (**Active State**).
- Quando ocorre uma falha, o dispositivo de Bypass da Viewtinet redireciona todo o tráfego e é dito estar em um estado de Bypass (**Bypass State**).
- O dispositivo de Bypass da Viewtinet pode ser configurado para funcionar tanto no Active State quanto no Bypass State sem nenhuma energia (ou seja, quando o cabo USB está desconectado).

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-2.png" align="center">
  <figcaption><b>Picture 2: The Bypass device in the Active State and in the Bypass State, respectively.</b></figcaption>
</figure>

<br />

### **MultiSegment**

O dispositivo de Bypass pode usar até 8 segmentos (dependendo de quantos módulos de hardware estão instalados). Cada segmento pode usar uma rota de tráfego de rede individual.

- Com a opção MultiSegment **disabled** (desativada), as mesmas configurações são aplicadas a todos os segmentos. Isso significa que contornar (bypassing) um Servidor do Appliance em um segmento (`FORCE_BYPASS`) também é aplicado a todos os outros segmentos.
- Com a opção MultiSegment **enabled** (ativada), cada segmento pode ser definido como `NORMAL_OPERATION` ou `FORCE_BYPASS` individualmente. Isso significa que o tráfego em um segmento pode ignorar (bypass) um Servidor do Appliance (`FORCE_BYPASS`), enquanto o tráfego em outro segmento é processado pelo Servidor do Appliance (`NORMAL_OPERATION`).

<br />
