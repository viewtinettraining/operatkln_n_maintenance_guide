---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'MFA Configuration'
id: MGK-93YX-ZIC-MJJ
slug: mfa-configuration
isVisible: true
lastUpdated: '2025-10-15 15:36:10'
---
# **<span align="center">Autenticação Multifator (MFA)</span>**

O MFA nativo do Viewtinet adiciona uma camada extra de segurança ao exigir que os usuários insiram um código de uso único enviado por e-mail após o login principal.

---

## **Pré-requisitos**

1.  **Integração SMTP**<br />
    Certifique-se de que o e-mail de saída esteja configurado em **Home → Configuration → Email Notifications**.<br />
    Isso permite o envio de códigos MFA através do seu servidor SMTP.

---

## **Configurar MFA na UI do Admin**

1.  **Abra Admin → Auth**
    
    <br />
    
    **Configuração do MFA (MFA Config)**
    
    -   **Usar script para envio de MFA (Use script for MFA mailing)**
        
        -   _Opcional_: marque para usar um script shell personalizado em vez do mailer embutido.
    -   **E-mail do Remetente (Sender Email)**
        
        -   Altere do padrão `support@viewtinet.com` para o seu endereço de caixa de correio real.
            
            -   Exemplo: `mfa@seudominio.com`
                
                <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/XZsC2aogPrsFViO1y4MW.png" align="center"></figure>
                
                <br />
                
    -   **Nome do Remetente (Sender Name)**
        
        -   Nome amigável que aparece no campo "De:" (From:) dos e-mails MFA, ex: `Equipe de Segurança`.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/6hhn0mElR79cvcetTucI.png"></figure>
    
    <br />
    
2.  **Salvar Alterações (Save Changes)**<br />
    Clique em **Save Changes** na parte inferior da página.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/Xv9eLSzBHhelDomkUqL2.png" align="center"></figure>
    
    <br />
    

---

## **Como Funciona**

-   Quando os usuários com MFA habilitado fazem login, eles recebem um e-mail contendo um código de uso único.
-   Eles devem inserir esse código na segunda tela para concluir a autenticação.

<br />