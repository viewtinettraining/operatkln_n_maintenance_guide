---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grupos'
id: JQS-NBVT-IRA-L3E
slug: groups
isVisible: true
lastUpdated: '2025-10-15 15:32:34'
---
# **<span align="center">Grupos (Groups)</span>**

<br />

<span align="justify">Enquanto as Funções (Roles) definem quais ações e visualizações um usuário pode acessar no Viewtinet, os Grupos (Groups) facilitam o gerenciamento de quem obtém essas funções. Os grupos são inteiramente internos ao Viewtimanager - eles não afetam a GUI diretamente, mas permitem atribuir (ou alterar) uma função para muitos usuários ao mesmo tempo.</span>

<br />

-   **Funções (Roles)** atribuem permissões (o que os usuários veem e podem fazer) e se integram a Provedores de Identidade externos (ex: Active Directory).
-   **Grupos (Groups)** reúnem os usuários para que você possa gerenciar suas funções em massa.

> **Por que usar Grupos?**<br />
> <span align="justify">Imagine que você tenha uma equipe de Administradores de Log que precisam de acesso total ao módulo Viewtilog, e outro conjunto de analistas que devem apenas poder visualizar painéis (dashboards) (mas não criá-los ou excluí-los). Se cada usuário estivesse sozinho, você teria que editar dez registros de usuário individualmente. Mas se você colocar todos os administradores de log em um grupo “Log-Admins” e os usuários apenas de painéis em um grupo “Report-Viewers”, você pode atribuir ou revogar a função apropriada no nível do grupo - e todos nesse grupo a herdam instantaneamente.</span>

Grupos são opcionais, mas altamente recomendados para grandes implantações ou mudanças frequentes de funções.

<br />

## **Página de Seleção de Grupos**

1.  No menu à esquerda, clique em **Admin**.
2.  Nas abas superiores, selecione **Groups**.<br />
    

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/4eCAgTWC2KlvkXlyRD9t.png"></figure>

<br />

## **Criar um novo Grupo**

1.  Clique em **\+ ADD NEW** na parte inferior da lista de grupos.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/LPqqImCR4ELROBZ1vbxj.png" align="center"></figure>
    

## **Preencher os Detalhes do Grupo**

-   **Name (Nome)**: Um identificador exclusivo para seu grupo (ex: `Log-Analysts`).
-   **Description (Descrição)** (opcional): Breves notas sobre o propósito do grupo.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/5MlUlUkPy5Dq4tXeTJuI.png" align="center"></figure>
    

<br />

## **Atribuir Funções ao Grupo**

1.  Expanda a seção **Group Roles** (Funções do Grupo).
2.  Na coluna **Available** (Disponível), marque a caixa ao lado de cada Função que você deseja que este grupo herde.
3.  Clique no botão com a seta simples **&gt;** para movê-las para **Selected** (Selecionado).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/3RaQpKMJpHhNvpKsybMp.png" align="center"></figure>

<br />

## **Salvar Suas Alterações**

Clique em **✔ SAVE CHANGES** na parte inferior para criar o grupo e aplicar suas Funções a todos os membros atuais (e futuros).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/kLmRaA2L41WM9INyXOmd.png" align="center"></figure>

<br />

<div class="sd-callout" data-callout-type="tip">Dica:<br>Ao adicionar ou remover um usuário de um grupo, ele ganha ou perde instantaneamente todas as Funções atribuídas a esse grupo - não são necessárias mais edições em sua conta de usuário individual.</div>

<br />