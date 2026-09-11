---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Bypass Extensions'
slug: bypass-extensions
isVisible: true
isSearchable: true
id: 9PX-AV4-WBK-OXM
---
# **<span align="center">Bypass Extensions</span>**

<br />

A guia **BYPASS EXTENSIONS** fornece uma lista dos plug-ins Bypasser disponíveis instalados no sistema. É importante observar que **esta página é estritamente informativa**, o que significa que ela exibe o status e a configuração básica das extensões, mas o estado operacional (ativado/desativado) é gerenciado a partir da guia Bypass Config ou em outras seções.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/networking-bypass-extensions-1.png" align="center"></figure>

<br />

---

## **How Bypass Extensions Work**

Um plug-in Bypasser funciona como um **Watchdog adicional** para o dispositivo. 

Enquanto o Watchdog Bypasser "principal" observa quaisquer alterações no processo do classificador ("The Probe"), um plug-in pode observar essencialmente qualquer coisa que produza um resultado "booleano" (ou seja, relatando **OK** ou **ERROR**).

### **Logical AND Operation**
Quando um ou mais plug-ins estão ativados, eles formam uma condição **"logical AND"** juntamente com o Watchdog Bypasser principal. Isso significa que:
- **TODOS** os resultados devem retornar `OK/READY` para que o Bypasser considere o sistema em um estado operacional normal.
- Se **pelo menos um** plug-in estiver falhando, o dispositivo de Bypass será imediatamente ajustado para `FORCE_BYPASS`.

### **Example: Viewtify OPT Plugin**
Por exemplo, o plug-in **Viewtify OPT** atua como um Watchdog especificamente para o serviço Viewtify OPT. 
Se esse plug-in for ativado, tanto o *The Probe* quanto o serviço *Viewtify OPT* devem relatar sucesso. Se qualquer um deles falhar, o Bypasser para de enviar batimentos cardíacos (heartbeats) e o dispositivo de Bypass é forçado para o estado `FORCE_BYPASS`.

---

## **Extension States**

Sempre há um número fixo de plug-ins implantados (disponíveis) que são instalados juntamente com o próprio Bypasser. No entanto, uma extensão pode ser ativada ou desativada:

- **Disabled Extension:** Não afeta o estado interno ou a tomada de decisão do Bypasser.
- **Enabled Extension:** Monitora ativamente seu serviço atribuído e pode forçar o sistema para bypass se detectar uma falha (conforme descrito no exemplo acima).

<br />