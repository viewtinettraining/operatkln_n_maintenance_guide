---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtify Business Groups'
id: BTJ-7EZ-LI3-8CP
slug: viewtify-business-groups
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 14:51:52'
---
# **<span align="center">Grupos de Negócios Viewtify (Viewtify Business Groups)</span>**

<br />

A aba **BUSINESS GROUPS** permite configurar Grupos de Negócios (BGs). Um Grupo de Negócios é uma dimensão editável usada para incluir as informações de sub-rede de seus clientes, agrupando IPs coletados pelo Viewtify com base em locais, filiais, departamentos ou qualquer outro critério de divisão relevante para sua organização.

<span align="justify">Por padrão, o Viewtify não contém nenhum Grupo de Negócios predefinido e não é obrigatório para a implantação. No entanto, é altamente recomendável incluir essas informações, pois existem otimizações e benefícios analíticos significativos com base nesses campos dentro do plugin Viewtify.</span>

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-bg-tab.png" align="center"></figure>

<br />

---

## **Configurando Grupos de Negócios**

Você tem duas maneiras principais de preencher a tabela de Grupos de Negócios:

1.  **Entrada Manual:** Você pode adicionar entradas individualmente clicando no botão **\+ ADD NEW BUSINESS GROUP** no canto inferior esquerdo. Isso cria uma nova linha onde você pode especificar manualmente a `Network` (endereço IP ou sub-rede CIDR) e o nome do `Business Group` correspondente.
2.  **Importação em Massa (Bulk Import):** Para implantações maiores, é muito mais eficiente usar o botão **IMPORT HOSTS** no canto inferior direito. Isso permite fazer o upload de uma lista de IPs e sub-redes em massa (via CSV) mapeados para seus respectivos grupos.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-bg-add.png" align="center"></figure>

<br />

Depois de adicionar ou importar suas redes, lembre-se de clicar no botão **SAVE CHANGES** para aplicar as novas definições de Grupo de Negócios.

---

## **Corrigindo Redes Sobrepostas (Fixing Overlapping Networks)**

Ao definir várias sub-redes, especialmente em redes corporativas complexas, é possível criar regras sobrepostas acidentalmente (ex., atribuir a sub-rede `192.168.1.0/24` a um grupo, mas atribuir especificamente a sub-rede menor `192.168.1.112/28` a outro).

O Viewtify implementa validações inteligentes para detectar e ajudar a resolver esses conflitos automaticamente. Se ocorrer uma sobreposição, um banner de aviso vermelho aparecerá na parte superior da tela explicando o conflito.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-bg-overlapping.png" align="center"></figure>

<br />

Para resolver o problema, basta clicar no botão roxo **FIX OVERLAPPING NETWORKS** localizado no canto superior direito da tabela. O sistema reordenará automaticamente as regras (movendo a sub-rede mais específica acima da mais ampla) para garantir que o tráfego seja categorizado corretamente sem ambiguidade.