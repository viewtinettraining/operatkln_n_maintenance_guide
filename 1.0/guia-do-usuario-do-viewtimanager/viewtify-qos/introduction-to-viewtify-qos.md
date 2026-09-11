---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Introdução ao Viewtify QoS'
id: G45-KCP-OW0-OSH
slug: introduction-to-viewtify-qos
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 11:13:26'
---
# **<span align="center">Introdução ao QoS do Viewtify</span>**

<br />

**Viewtify QoS** é o módulo avançado de gerenciamento de largura de banda e Qualidade de Serviço da Viewtinet. Ele fornece aos administradores controle preciso sobre o tráfego da rede, garantindo que os aplicativos críticos recebam os recursos necessários e, ao mesmo tempo, limitando o impacto das transferências de dados não essenciais.

Através do QoS do Viewtify, você pode criar e aplicar poderosas políticas de tráfego, incluindo:

-   **Rate-Limiting (Limitação de Taxa):** Restringir a largura de banda máxima disponível para usuários, IPs ou aplicativos específicos.
-   **Traffic Shaping (Modelagem de Tráfego):** Suavizar rajadas de tráfego para manter um fluxo de dados constante e previsível.
-   **Prioritization (Priorização):** Dar preferência ao tráfego de missão crítica (como VoIP ou videoconferência) em relação ao tráfego de prioridade mais baixa (como downloads de arquivos).
-   **Dropping (Descarte):** Bloquear completamente ou descartar tráfego indesejado ou malicioso.

<br />

---

## **Dependência do Viewtimon**

> <div class="sd-callout" data-callout-type="alert">O módulo QoS do Viewtify está fundamentalmente ligado à engine de DPI do <strong>Viewtimon</strong>.</div>

**É obrigatório implantar o Viewtimon** para usar o QoS do Viewtify. Isso ocorre porque o Viewtify depende inteiramente das capacidades de inspeção profunda de pacotes (DPI) do Viewtimon para classificar com precisão o tráfego que atravessa a rede. O Viewtimon identifica os aplicativos, protocolos e usuários e, em seguida, o Viewtify aplica as políticas de gerenciamento de largura de banda correspondentes com base nessa classificação.

<br />

---

## **Implantação Inline e Bypasser**

Ao contrário das ferramentas tradicionais de monitoramento que podem operar passivamente em uma porta espelhada, o QoS do Viewtify é um mecanismo de controle ativo. Portanto, ele deve ser implantado **inline** (em linha) com o tráfego de rede.

Para garantir a alta disponibilidade da rede e evitar que o appliance da Viewtinet se torne um ponto único de falha, o QoS do Viewtify é implantado em conjunto com um **bypasser de hardware**. O bypasser garante que se o appliance perder energia ou o serviço Viewtify for interrompido, o tráfego da rede ignorará fisicamente o appliance e continuará fluindo sem interrupção.

_(A configuração e o gerenciamento específicos do bypasser serão explicados em detalhes nas seções subsequentes)._