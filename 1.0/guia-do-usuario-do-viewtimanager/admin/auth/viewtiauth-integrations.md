---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Integrações do Viewtiauth'
id: ZIC-1AVN-68A-KLJ
slug: viewtiauth-integrations
isVisible: true
lastUpdated: '2025-10-15 15:37:12'
---
# **<span align="center">Integrações do Viewtiauth</span>**

<br />

A seção de Integrações do Viewtiauth define como o Viewtinet autentica os usuários, especificando um ou mais backends de autenticação, sua precedência e a função padrão atribuída no login bem-sucedido. O Viewtiauth processa as entradas em ordem crescente (`1` = maior precedência). Se uma entrada for marcada como Inativa (Inactive) ou se a autenticação falhar nesse backend, ele fará o fallback (retorno) para a próxima entrada ativa.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/D0gtafaAW98qdp3xdHbr.png" align="center"></figure>

<br />

## **Campos de Configuração**

<table><tbody><tr><th><p>Campo</p></th><th><p>Descrição</p></th></tr><tr><td><p><strong>Active (Ativo)</strong></p></td><td><p>Habilite (☑) ou desabilite (☐) este backend de autenticação. Entradas inativas são ignoradas.</p></td></tr><tr><td><p><strong>Order (Ordem)</strong></p></td><td><p>Precedência deste backend (número inteiro). Os números menores são tentados primeiro. Por exemplo, <code>1</code> é a prioridade mais alta.</p></td></tr><tr><td><p><strong>Type (Tipo)</strong></p></td><td><p>Método de autenticação:</p></td></tr></tbody></table>

-   `ad` (Active Directory)
-   `local` (banco de dados interno do Viewtinet)
-   `ldap` (servidor LDAP externo)
-   `saml2` (SAML 2.0 IdP) | | **Default Role (Função Padrão)**| Função atribuída automaticamente aos usuários autenticados por este backend. Selecione qualquer função definida em **Admin ➔ Roles**. |

<br />

## **Fluxo de Autenticação**

1.  O Viewtiauth lê todas as entradas configuradas, classificadas de forma crescente por **Order**.
2.  Para cada entrada em sequência:
    
    -   Se **Active** estiver desmarcado, pule para o próximo.
    -   Caso contrário, tente a autenticação usando o **Type** especificado.
    -   Em caso de sucesso, atribua a **Default Role** e conceda o acesso.
    -   Em caso de falha, mova para a próxima entrada ativa.
3.  Se todas as entradas ativas falharem, a autenticação é negada.

> **Exemplo:**
> 
> -   Entrada `Order = 1`, **Active** = ☐ (inativo)
> -   Entrada `Order = 2`, **Active** = ☑, **Type** = `local`
> -   Entrada `Order = 3`, **Active** = ☑, **Type** = `ldap`
> -   Entrada `Order = 4`, **Active** = ☐ (inativo)
> 
> O Viewtiauth tentará primeiro o banco de dados **local** (ordem 2). Se o usuário não for encontrado ou a senha estiver incorreta, ele tentará o servidor LDAP (ordem 3).

<br />

## **Salvando Suas Alterações**

1.  Após ajustar **Active**, **Order**, **Type** ou **Default Role**, clique em **Save Changes** na parte inferior da página.
2.  Uma mensagem de confirmação aparecerá assim que a nova sequência de autenticação for aplicada.

> **Nota:** As alterações feitas aqui afetam como **todos** os usuários se autenticam. Tenha cuidado ao desabilitar ou reordenar as entradas para evitar o bloqueio inadvertido do acesso administrativo.

<br />