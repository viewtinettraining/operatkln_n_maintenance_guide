---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Políticas de QoS'
id: ZXW-9YD-UAF-XIM
slug: policies
isVisible: true
isSearchable: true
lastUpdated: '2026-05-27 16:45:17'
---
# **<span align="center">Políticas de QoS</span>**

<br />

A seção de **Políticas** é onde a mágica acontece. É o quadro onde você vincula suas Regras de Classificação com seus Perfis de QoS para construir a lógica final que a engine do Viewtify irá executar.

<br />

## **Árvore de Hierarquia Visual**

O QoS do Viewtify representa suas políticas de rede como uma árvore de hierarquia de vários níveis, visual e intuitiva. O tráfego flui da raiz da árvore para baixo através dos ramos, sendo avaliado em cada nó até encontrar uma correspondência.

### Visão Detalhada

Ao marcar a caixa **Detailed View** no topo, os nós na árvore se expandem para mostrar exatamente os intervalos de IP, regras e limites de largura de banda configurados em cada etapa única, permitindo que você veja todos os detalhes da política em um relance.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_15_img_1.png" align="center"></figure>

<br />

---

## **Adicionando e Editando Políticas**

As políticas são criadas dentro de uma estrutura de árvore onde o nó pai é o próprio Caso de Uso. A partir daí, ele se ramifica em nós filhos e irmãos (no mesmo nível). O aplicativo é totalmente capaz de capturar erros lógicos durante a criação dessas políticas.

### **Como Criar uma Política**

1.  **Localize o nó de destino:** Encontre o nó (ex., a raiz do Caso de Uso ou uma política existente) sobre o qual você deseja criar a nova política.
2.  **Clique com o botão esquerdo no nó:** Esta ação abrirá um menu de contexto.<br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-create-1.png" align="center"></figure>
    
    <br />
    
3.  **Selecione "Add Child Policy":** No menu aberto, clique nesta opção.<br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-create-2.png" align="center"></figure>
    
    <br />
    
4.  **Configure as Regras de Classificação:** Uma nova tela será aberta para configurar a política. Na primeira seção, você configura as regras de classificação.
    
    -   Você pode definir regras por IP, Intervalos de IP, Sub-redes, Portas, Protocolos, etc. Elas podem ser aplicadas como iniciadores de conexão ou destinos de conexão.
    -   Além disso, você deve selecionar o **Classification Type**:
        
        -   **Application:** O tráfego é classificado com base nas regras individuais configuradas para um aplicativo especificamente selecionado.<br />
            
            <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-create-3.png" align="center"></figure>
            
            <br />
            
        -   **Application Group:** Neste caso, o tráfego será classificado para todo o grupo de aplicativos selecionado.<br />
            
            <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-create-4.png" align="center"></figure>
            
5.  **Adicione Várias Regras e Descrição:** Você pode adicionar várias regras de classificação à mesma política clicando no botão **+ ADD NEW RULE**, desde que o tipo de aplicativo (Application ou Application Group) permaneça o mesmo para todas as regras dentro desse nó. Além disso, você pode adicionar uma descrição personalizada no campo **Connector description** para identificar melhor o propósito da política.<br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-create-5.png" align="center"></figure>
    
6.  **Selecione um Perfil e Configure seu Agendamento:** Uma vez definidas as regras de classificação, o próximo passo é escolher o perfil (a ação a ser tomada quando as regras forem atendidas) na seção de **Profiles** abaixo.
    
    -   **Default Profile:** Por padrão, um perfil é atribuído com o agendamento "default", o que significa que se aplica 24/7, independentemente da hora e dia. Você pode alterar este perfil selecionando o perfil desejado no menu suspenso.<br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-profile-1.png" align="center"></figure>
        
        <br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-profile-2.png" align="center"></figure>
        
        <br />
        
    -   **Adicionando um Perfil Agendado:** Se você quiser aplicar um perfil diferente (ou o mesmo), mas restrito a um agendamento específico, clique no botão **+ ADD NEW PROFILE**.
    -   **Modificando o Agendamento:** Após adicionar uma nova entrada de perfil, clique no **ícone de lápis** ao lado dela para editar seu intervalo de tempo.<br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-profile-3.png" align="center"></figure>
        
        <br />
        
    -   Você será solicitado a configurar o **Start Time** e o **End Time** exatos para quando este perfil específico deve estar ativo.<br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-profile-4.png" align="center"></figure>
        
        <br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-profile-5.png" align="center"></figure>
        

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtify-policies-example-1.png" align="center"></figure>

### **Exemplo de Criação de Política**

Vamos ver um exemplo prático de uma configuração de política concluída com base nas etapas acima.

Na imagem a seguir, criamos uma política que:

1.  **Classifica o tráfego:** Ela visa especificamente conexões originadas do **Range Test 1** (IPs `10.30.24.141` a `10.30.24.146`) quando eles se conectam ao aplicativo **facebook**.
2.  **Aplica um perfil padrão:** Um perfil padrão (`Max_Rate_10Mbps`) limita sua largura de banda a **10 Mbps** por padrão (24/7).
3.  **Aplica um perfil agendado:** No entanto, adicionamos uma segunda entrada de perfil (`Max_Rate_50Mbps`) que concede a eles um limite de largura de banda superior de **50 Mbps**, mas estritamente durante o horário de folga, das **06:00 PM às 08:00 AM**.

---

## **Validações de Política**

Como as políticas são avaliadas sequencialmente, a sua ordem estrutural é muito importante. O QoS do Viewtify inclui validações rigorosas para evitar erros lógicos.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_23_img_1.png" align="center"></figure>

<br />

-   **Destaque de Erros:** Se as alterações nos perfis criarem problemas (como atribuir um perfil que não existe mais ou alocar mais largura de banda Min Rate do que o nó pai tem disponível), um erro de validação impedirá o salvamento, e o nó afetado será destacado em vermelho.
-   **Aviso de Regras Mascaradas:** O sistema irá avisá-lo se uma regra de classificação altamente específica for colocada _abaixo_ de uma regra muito genérica (ex., colocar uma regra de IP abaixo de uma regra "Qualquer IP"), o que significa que a regra específica nunca seria alcançada.
-   **Posicionamento do App-ID:** As políticas baseadas exclusivamente no Application ID (assinaturas de DPI) devem ser colocadas na posição mais à direita, antes do nó "Others".

<br />