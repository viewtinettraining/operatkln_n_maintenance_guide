---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Pré-requisitos'
id: K8S-P9GS-SJQ-339
slug: prerequisites
isVisible: true
lastUpdated: '2025-10-15 14:58:01'
---
# **<span align="center">Pré-requisitos</span>**

<span align="justify">Antes que você possa usar efetivamente o recurso Configuration Manager no Viewtinet, é essencial preparar seu inventário e credenciais de acesso. Este capítulo descreve os pré-requisitos necessários e os passos para verificá-los dentro do módulo Inventory (Inventário).</span>

## **1\. Dispositivos Adicionados ao Inventário**

<span align="justify">Certifique-se de que todos os dispositivos a serem gerenciados sejam adicionados ao Inventário. Os dispositivos podem ser importados por meio de arquivos CSV, descoberta automática (autodiscovery) ou adicionados manualmente.</span>

<span align="justify">O processo detalhado de provisionamento de dispositivos no inventário é explicado no capítulo de Inventário.</span>

<span align="justify">Na aba de visão geral do Inventário (Inventory overview), você verá uma lista de dispositivos, juntamente com detalhes importantes, como endereço IP, nome do dispositivo, grupos OID, sistema operacional, versão do software, tipo de dispositivo e fabricante (vendor).</span>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/7JRNcefCYxntnLB9GEUl.png" align="center"></figure>

<br />

## **2\. Filtragem de Dispositivos**

<span align="justify">Para utilizar o recurso Configuration Manager, é necessário ter um filtro criado que selecione os dispositivos a serem incluídos. Esse filtro define o subconjunto de dispositivos em que as tarefas de configuração atuarão.</span>

<span align="justify">A criação e o gerenciamento de filtros são explicados em detalhes no capítulo de Inventário. Os filtros permitem direcionar dispositivos com base em atributos como fabricante, sistema operacional, endereço IP ou outros metadados.</span>

<span align="justify">Os filtros também podem ser combinados com operadores lógicos (AND, OR, NOT) para refinar com precisão a seleção do dispositivo.</span>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/CglaXww1LUAHyUeKk61W.png"></figure>

## **<span class="text-large"><br></span>3\. Configuração das Credenciais de Acesso**

<span align="justify">As credenciais podem ser adicionadas usando o modelo de provisionamento do Viewtinet ou importando seu próprio arquivo CSV.</span>

<span align="justify">Se essas credenciais não tiverem sido importadas usando os métodos mencionados acima, será necessário criá-las manualmente no módulo Inventário.</span>

<span align="justify">Na aba Credentials (Credenciais) do Inventário, verifique se você definiu as credenciais necessárias, incluindo:</span>

-   <span align="justify">Credenciais de acesso SSH (porta, nome de usuário, tipo de autenticação, senha ou chave)</span>
-   <span align="justify">Credenciais de acesso Telnet, se aplicável</span>

Para criar uma nova credencial, clique no botão \*\*"ADD New Credential"\*\* e configure os parâmetros de conexão dos dispositivos que você deseja incluir no recurso Configuration Manager.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/KoHQmqrgo6kiFPG0xxH6.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/TjGu5czRScCowR8e813J.png" align="center"></figure>

<br />

<figure align="center" style="width:21%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/NqihyBDVhoNO9q2M083d.png" width="21%" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/k15mESrCcY2Xh7Xx5xQR.png" align="center"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/gWSh77BV9Og7ynvzpMaB.png"></figure>

<br />

## **4\. Relações entre Dispositivo e Credencial**

<span align="justify">Por fim, atribua as credenciais aos dispositivos criando relações (relations) na aba Relations. Esse mapeamento é necessário para que o Configuration Manager saiba quais credenciais usar para acessar cada dispositivo.</span>

<span align="justify">Na aba Relations, filtre os dispositivos e as credenciais para atribuí-los de acordo.</span>

<br />

Assim que esses pré-requisitos forem atendidos — dispositivos adicionados, filtrados, credenciais configuradas e relações atribuídas — você terá a configuração necessária para criar e executar tarefas de configuração no recurso Configuration Manager.

---

Essa preparação garante um gerenciamento seguro, direcionado e eficiente das configurações de dispositivos em sua rede.