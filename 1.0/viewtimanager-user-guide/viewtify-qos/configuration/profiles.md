---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'QoS Profiles'
id: WO0-VUU-YUB-DSJ
slug: profiles
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 15:34:26'
---
# **<span align="center">Perfis de QoS</span>**

<br />

Se as Regras de Classificação definem _qual_ tráfego você está gerenciando, os **Perfis de QoS** definem _como_ esse tráfego deve ser tratado. Ao atribuir um perfil a uma regra, você instrui a engine sobre como moldar, limitar ou priorizar o fluxo.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-1.png" align="center"></figure>

<br />

---

## **Tipos de Perfis**

O QoS do Viewtify oferece seis tipos fundamentais de perfis para atender a diferentes necessidades de rede:

1.  **Max Rate:** Define um limite máximo de taxa de transferência para aplicativos não críticos ou pesados (ex., limitando downloads de streaming ou P2P) para evitar que eles saturem o link.
2.  **Max Rate (%):** Usado geralmente em políticas filhas para definir um limite máximo de taxa de transferência como uma porcentagem da largura de banda da política pai.
3.  **Min Rate:** Aloca uma quantidade mínima garantida de largura de banda para aplicativos críticos, garantindo que eles funcionem perfeitamente mesmo durante o congestionamento da rede.
4.  **Min Rate (%):** Usado geralmente em políticas filhas para definir uma largura de banda mínima garantida como uma porcentagem da largura de banda da política pai.
5.  **Priority Queue:** Define diferentes prioridades de transmissão de acordo com a sensibilidade dos fluxos.
6.  **Drop:** Descarta instantaneamente os pacotes de fluxos indesejados ou maliciosos, bloqueando efetivamente o tráfego.
7.  **Normal QoS:** Deixa as configurações de QoS herdadas intactas, sem aplicar novas restrições neste nível.
8.  **Real Time:** Criado e otimizado especificamente para aplicativos de conferência, voz e VoIP para garantir latência mínima.
9.  **No QoS:** Nenhum QoS é definido para o fluxo. Em caso de saturação do link, esses pacotes são os mais propensos a serem descartados pelo hardware de rede.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-2.png" align="center"></figure>

<br />

---

## **Níveis de Prioridade**

Ao usar perfis Priority Queue, há **3 níveis de prioridade principais** disponíveis: High, Medium e Low.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-3.png" align="center"></figure>

<br />

-   **Aplicação Hierárquica:** As prioridades são aplicadas de forma hierárquica. Cada nível herda a prioridade de seus níveis mais altos dentro da árvore de políticas.
-   **Combinações Lógicas:** Por meio da combinação de prioridades em diferentes ramos da sua árvore de políticas, você pode criar até **16 níveis de prioridade lógica** para um gerenciamento de tráfego extremamente granular.

<br />

---

## **Taxas Simétricas e Assimétricas**

Ao configurar os limites de largura de banda, você tem a flexibilidade de definir como o tráfego de upload e download será tratado.

-   **Taxas Combinadas:** As taxas Máx e Mín podem ser aplicadas dentro do mesmo perfil para o tráfego de entrada e de saída, reduzindo o número total de regras necessárias em sua política.
-   **Simetria:** Você pode configurar o perfil com taxas **Simétricas** (ex., 200 Kbps down / 200 Kbps up) ou taxas **Assimétricas** (ex., 14 Mbps down / 12 Mbps up) usando o botão de alternância de igual/diferente entre os campos.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-4.png" align="center"></figure>

<br />

---

## **Criando um Perfil de QoS**

Para criar e configurar um perfil de QoS com base nas necessidades da sua rede, siga estas etapas:

1.  Clique no botão **+ ADD NEW** para criar uma nova linha.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-create-1.png" align="center"></figure>

<br />

2.  Insira um **Name** único para o seu perfil. Se você tentar salvar sem preencher os campos obrigatórios, o sistema destacará a linha em vermelho.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-create-2.png" align="center"></figure>

<br />

3.  Selecione o **Type** no menu suspenso (ex., `Max Rate`).
4.  Nas caixas **Download/Priority** e **Upload**, insira a largura de banda que você deseja controlar (ex., `300 Kbps`). Por padrão, o perfil será **Symmetric**, o que significa que as taxas de Download e Upload são iguais.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-create-3.png" align="center"></figure>

<br />

5.  Se você precisar configurar um perfil **Assimétrico** (onde os limites de Download e Upload são diferentes), clique no símbolo de igual (`=`) entre as caixas.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-create-4.png" align="center"></figure>

<br />

6.  O símbolo mudará para um sinal de diferente (`≠`), permitindo que você configure a velocidade de upload independentemente, de acordo com suas necessidades.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-create-5.png" align="center"></figure>

<br />

---

## **Pesquisando e Excluindo Perfis**

Da mesma forma que nas regras de classificação, validações de segurança evitam que você quebre configurações ativas.

-   Os Perfis de QoS podem ser excluídos **apenas se não estiverem em uso** em nenhuma política.
-   A opção de **Search** (lupa) ajuda você a encontrar exatamente qual política está usando o perfil no momento, para que você possa reatribuí-lo antes de tentar a exclusão.

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-search.png" align="center">
</figure>

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-search-result.png" align="center">
</figure>

<br />

Para excluir um perfil, localize o perfil desejado e clique no **ícone de lixeira**. No entanto, se um perfil estiver sendo usado atualmente em um Caso de Uso ou Política, o sistema o protegerá e não será possível excluí-lo.

<br />

<figure align="center">
  <img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-profiles-delete.png" align="center">
</figure>

<br />