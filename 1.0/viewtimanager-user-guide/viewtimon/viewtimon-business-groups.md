---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtimon Business Groups'
id: APK-WHS-YOA-AUX
slug: viewtimon-business-groups
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 12:06:00'
---
# **<span align="center">Grupos de Negócios do Viewtimon</span>**

<br />

A guia **BUSINESS GROUPS** permite configurar Grupos de Negócios (BGs). Um Grupo de Negócios é uma dimensão editável usada para incluir as informações de sub-rede de seus clientes, agrupando os IPs coletados pelo Viewtimon com base em localizações, filiais, departamentos ou quaisquer outros critérios de divisão relevantes para a sua organização.

Por padrão, o Viewtimon não contém nenhum Grupo de Negócios predefinido e não é obrigatório para a implantação. No entanto, é altamente recomendável incluir essas informações, pois há otimizações significativas e benefícios analíticos baseados nesses campos dentro do plugin do Viewtimon.

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-bg-tab.png" align="center">
</figure>

<br />

---

## **Configurando Grupos de Negócios**

Você tem duas maneiras principais de preencher a tabela de Grupos de Negócios:

1.  **Entrada Manual:** Você pode adicionar entradas individualmente clicando no botão **+ ADD NEW BUSINESS GROUP** no canto inferior esquerdo. Isso cria uma nova linha onde você pode especificar manualmente a `Network` (endereço IP ou sub-rede CIDR) e o respectivo nome do `Business Group`.
2.  **Importação em Lote:** Para implantações maiores, é muito mais eficiente usar o botão **IMPORT HOSTS** no canto inferior direito. Isso permite que você faça o upload de uma lista de IPs e sub-redes em lote (via CSV) mapeados para seus respectivos grupos.

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-bg-add.png" align="center">
</figure>

<br />

Depois de adicionar ou importar suas redes, lembre-se de clicar no botão **SAVE CHANGES** para aplicar as novas definições do Grupo de Negócios.

---

## **Corrigindo Redes Sobrepostas**

Ao definir várias sub-redes, especialmente em redes corporativas complexas, é possível criar regras sobrepostas acidentalmente (por exemplo, atribuir a sub-rede `192.168.1.0/24` a um grupo, mas atribuir especificamente a sub-rede menor `192.168.1.112/28` a outro).

O Viewtimon implementa validações inteligentes para detectar e ajudar a resolver esses conflitos automaticamente. Se ocorrer uma sobreposição, um banner de aviso vermelho aparecerá na parte superior da tela explicando o conflito.

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-bg-overlapping.png" align="center">
</figure>

<br />

Para resolver o problema, basta clicar no botão roxo **FIX OVERLAPPING NETWORKS** localizado no canto superior direito da tabela. O sistema reordenará automaticamente as regras (movendo a sub-rede mais específica para cima da mais abrangente) para garantir que o tráfego seja categorizado corretamente sem ambiguidade.
