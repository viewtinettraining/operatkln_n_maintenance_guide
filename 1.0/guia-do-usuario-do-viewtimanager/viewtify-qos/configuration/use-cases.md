---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Casos de Uso'
id: GJV-9YI-K8L-7S9
slug: use-cases
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 15:00:50'
---
# **<span align="center">Casos de Uso</span>**

<br />

No QoS do Viewtify, cada árvore de política inteira que você constrói e salva é armazenada como um **Caso de Uso**. Essa estrutura permite que você mantenha vários designs de política de rede diferentes simultaneamente, sem perder seu trabalho. Uma **Árvore de Políticas** é a estrutura hierárquica onde você define as diferentes regras de gerenciamento de tráfego, vinculando regras de classificação a perfis de QoS, determinando prioridades e alocações de largura de banda para cada tipo de tráfego.

<br />

---

## **Criando um Caso de Uso**

Para adicionar um novo Caso de Uso, siga estas etapas:

1.  No Home de Configuração, clique no botão **POLICIES**.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-use-cases-create-0.png" align="center"></figure>

<br />

2.  Clique no botão **+ ADD NEW USE CASE**.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-use-cases-create-1.png" align="center"></figure>

<br />

3.  Isso o levará à seção de configuração do Caso de Uso. Aqui você deve inserir um nome descritivo e configurar tanto a **Download bandwidth** quanto a **Upload bandwidth**. **Nota:** Isso representa a largura de banda total máxima que estará disponível para este Caso de Uso específico.
4.  Clique em **SAVE** para gerar e salvar a alteração no nível de estrutura da política.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-qos-use-cases-create-2.png" align="center"></figure>

<br />

5.  Essa ação o levará à tela onde você pode começar a construir a árvore de políticas (este processo será explicado em detalhes posteriormente).
6.  Uma vez que seu Caso de Uso e a árvore de políticas estiverem prontos, você deve clicar no botão **APPLY QOS**. Esta etapa final é o que realmente aplica e impõe o Caso de Uso, juntamente com todas as suas políticas criadas, no tráfego da rede.

<br />

---

## **Gerenciando Vários Casos de Uso**

A plataforma tem a capacidade de armazenar vários Casos de Uso (sendo cada um, um conjunto completo de políticas), mas **apenas um pode estar ativo por vez**. 

Para ativar um Caso de Uso ou mudar para um diferente, basta seguir estas etapas:
1. Selecione o Caso de Uso desejado no menu suspenso.
2. Clique no botão **APPLY QOS**.

O Caso de Uso atualmente ativo será marcado com a palavra **(active)** no menu suspenso.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-dropdown.png" align="center"></figure>

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-apply.png" align="center"></figure>

<br />

---

## **Exportando e Importando**

As implantações de rede frequentemente abrangem vários locais ou exigem a migração de configurações entre diferentes instâncias do Viewtimanager. Esse recurso também é altamente útil para criar **backups** de suas políticas, permitindo que você recupere rapidamente todo o seu conjunto de políticas em caso de um desastre ou de um caso de uso corrompido.

### **Como Exportar um Caso de Uso**
1. Clique no **nó pai** (o nó mais alto) de toda a árvore de políticas.
2. No menu de contexto, clique em **Export Use Case**.
3. A configuração será salva em seu disco local como um arquivo JSON.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-export.png" align="center"></figure>

<br />

### **Como Importar um Caso de Uso**
1. Clique no botão **IMPORT USE CASE** localizado na parte superior direita da tela.
2. Selecione o arquivo de backup exportado anteriormente no seu disco local para restaurar ou replicar a árvore de políticas.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-import.png" align="center"></figure>

<br />

---

## **Visão de Histórico**

Para rastrear as alterações históricas feitas em seus Casos de Uso e políticas, você pode utilizar a funcionalidade de **History View**.

- Clique no botão **SWITCH TO HISTORY VIEW** para acessar este recurso.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-history-1.png" align="center"></figure>
  <br />

- Depois de ativado, o menu suspenso principal apresentará uma lista cronológica de alterações e casos de uso aplicados.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-history-2.png" align="center"></figure>
  <br />

- Para retornar à lista padrão de casos de uso ativos e rascunhos, basta clicar no botão **SWITCH TO USE CASES VIEW**.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-history-3.png" align="center"></figure>

<br />

---

## **Pesquisar dentro de um Caso de Uso**

À medida que suas árvores de políticas se tornam mais complexas, você pode facilmente localizar elementos específicos usando a ferramenta de pesquisa integrada. Esse recurso permite que você encontre um IP, uma regra de classificação ou um perfil de QoS.

Para usar a ferramenta de pesquisa:
1. Digite seus critérios de pesquisa na **caixa de pesquisa** localizada acima da área da árvore de políticas.
2. O sistema destacará automaticamente o nó correspondente e traçará o caminho desde o nó pai até o resultado.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-search.png" align="center"></figure>

<br />

---

## **Visão Detalhada**

Para inspecionar as configurações mais profundas de seu Caso de Uso, você pode habilitar a funcionalidade de **Detailed View**. 

- Ao clicar na caixa de seleção **Detailed View** localizada acima da árvore, a representação visual se expandirá.
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-detailed-1.png" align="center"></figure>
  <br />

- A visualização expandida exibe informações detalhadas diretamente no quadro, incluindo parâmetros específicos para nós, conectores e políticas (como taxas máximas exatas de up/down, subconjuntos de IP configurados e IDs de componentes).
  <br />
  <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-usecases-detailed-2.png" align="center"></figure>

<br />