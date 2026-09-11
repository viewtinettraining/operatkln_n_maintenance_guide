---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Interfaces
slug: interfaces
isVisible: true
isSearchable: true
id: UW1-KO1-P3S-7TC
---
# **<span align="center">Interfaces</span>**

<br />

A guia **Interfaces** exibe todas as interfaces físicas disponíveis na máquina, juntamente com a configuração atual e o status. Esta visualização é essencial para identificar quais interfaces estão atribuídas aos diferentes módulos DPI e QoS.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-interfaces-1.png" align="center"></figure>

<br />

---

## **Key Information Displayed**

Para cada interface física, o sistema fornece os seguintes detalhes:

- **ID, Name, and Interface:** Identifica a porta de hardware, seu nome no sistema e uma breve descrição do controlador (ex., *Ethernet Controller*).
- **Driver:** Exibe o driver atualmente usado pela interface. É fundamental observar que o driver **`igb_uio`** é especificamente necessário para interfaces associadas aos módulos **Viewtimon** e **Viewtify QoS** para garantir o processamento de pacotes de alto desempenho adequado.
- **Module Assignment (Viewtimon / Viewtify QoS):** Caixas de seleção indicam a qual módulo a interface está atribuída no momento. As interfaces podem ser alocadas tanto ao Viewtimon (para monitoramento) quanto ao Viewtify QoS (para controle de tráfego).
- **Status:** Mostra o status do link físico da interface:
  - 🟢 **Green Circle:** A interface está fisicamente **UP** (conectada).
  - ⚪ **Gray Circle:** A interface está fisicamente **DOWN** (desconectada).

<br />