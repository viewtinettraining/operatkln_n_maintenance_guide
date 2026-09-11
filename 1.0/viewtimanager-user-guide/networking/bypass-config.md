---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Bypass Configuration'
slug: bypass-config
isVisible: true
isSearchable: true
id: DVT-MAD-BHQ-LDF
---
# **<span align="center">Bypass Configuration</span>**

<br />

A guia **BYPASS CONFIG** permite que você defina o comportamento dos segmentos de rede (pares de portas físicas). A partir desta tela, você pode gerenciar como o tráfego é tratado pelo dispositivo, processando-o normalmente ou ignorando-o (bypassing) completamente.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-config-1.png" align="center"></figure>

<br />

---

## **Global vs. Per-Segment Bypass**

A funcionalidade de bypass pode ser controlada globalmente para todo o dispositivo ou individualmente por segmento.

- **Global Bypass:** Você pode colocar todo o dispositivo no modo bypass usando a chave global.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-config-3.png" align="center"></figure>
  <br />

- **Multi-segment Feature:** Quando o recurso de múltiplos segmentos está ativado, você pode configurar as opções de bypass para cada segmento individualmente. Isso permite definir segmentos específicos para *Normal Operation* enquanto força outros para *Bypass*.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-config-4.png" align="center"></figure>
  <br />

---

## **Per-Segment Configuration Options**

Expandir um segmento fornece diversas opções avançadas de configuração adaptadas a necessidades de rede específicas:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-config-2.png" align="center"></figure>

<br />

- **Use VLANs:** 
  - Ao ativar esta caixa de seleção, o motor de QoS classificará a origem das conexões internas com base na tag de VLAN do pacote. 
  - Em ambientes QinQ, a VLAN mais externa será lida. 
  - *Default Behavior:* Se desabilitado, o motor de QoS classifica a origem da conexão usando o endereço IP.

- **Extensions:** Estes menus suspensos permitem que você configure extensões para casos de uso especiais.

- **Use Fail Port:** 
  - Quando ativado, se uma das duas portas no segmento falhar, o sistema desativará automaticamente a porta par (peer port) desse segmento. Isso força o segmento inteiro para o modo bypass, garantindo a continuidade do tráfego.

- **One failure is enough:** 
  - Ativar esta opção garante que o segmento entre no modo bypass imediatamente após uma única falha. Isso evita problemas de "flapping" na rede, onde quedas intermitentes de link poderiam fazer o dispositivo entrar e sair constantemente do modo bypass.

<br />