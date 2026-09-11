---
reusableId: 67
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Configuração do Sistema Operacional'
id: DM2-XF36-ELR-TFC
slug: operating-system-setup
isVisible: true
lastUpdated: '2025-10-14 09:43:46'
---
# **<span align="center">Configuração do Perfil do Sistema Operacional</span>**

Nesta etapa, você configurará o perfil de usuário padrão para a instalação do sistema operacional.

Todos os módulos, contêineres e serviços do Viewtinet são executados sob o usuário dedicado `viewtinet`. Portanto, é **obrigatório** criar este usuário exatamente como especificado abaixo. O nome do host do servidor e a senha do usuário ficam a critério do administrador.

---

## **Criando o Usuário Viewtinet e Definindo o Hostname**

Durante a instalação do Ubuntu Server, você encontrará a tela de **Configuração de Perfil**. Preencha os campos da seguinte forma:

-   **Seu nome:**<br />
    Insira `viewtinet`.
-   **Nome do seu servidor:**<br />
    Insira o hostname desejado. Este hostname é como o servidor se identificará em sua rede.
-   **Escolha um nome de usuário:**<br />
    Insira `viewtinet`. _(Este nome de usuário é obrigatório.)_
-   **Escolha uma senha:**<br />
    Insira uma senha forte e segura seguindo as diretrizes de segurança de sua organização.
-   **Confirme sua senha:**<br />
    Re-insira a senha para confirmar.

Certifique-se de que todos os campos estejam corretamente preenchidos conforme mostrado no exemplo abaixo:

<br />

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/hFmxz31pTGJmrTg53sRY.png"></figure>

Depois que os campos forem preenchidos, selecione `[Concluído]` para prosseguir com a instalação.

---

**Importante:**

-   Não desvie do uso de `viewtinet` como nome de usuário do sistema, pois isso é necessário para o funcionamento correto da plataforma.
-   Certifique-se de que a senha definida esteja em conformidade com as políticas de senha de sua organização.

Prossiga para os capítulos seguintes após concluir a configuração do perfil.

---

<br />
