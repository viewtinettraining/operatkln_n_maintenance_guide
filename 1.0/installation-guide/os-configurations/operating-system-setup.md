---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Operating System Setup'
id: DM2-XF36-ELR-TFC
slug: operating-system-setup
isVisible: true
lastUpdated: '2025-10-14 09:43:46'
---
# **<span align="center">Configuração de Perfil do Sistema Operacional</span>**

Nesta etapa, você configurará o perfil de usuário padrão para a instalação do sistema operacional.

Todos os módulos, contêineres e serviços do Viewtinet são executados sob o usuário dedicado `viewtinet`. Portanto, é **obrigatório** criar este usuário exatamente como especificado abaixo. O nome de host do servidor e a senha do usuário ficam a seu critério.

---

## **Criando o Usuário Viewtinet e Definindo o Hostname**

Durante a instalação do Ubuntu Server, você encontrará a tela **Profile setup** (Configuração de perfil). Preencha os campos da seguinte maneira:

-   **Your name (Seu nome):**<br />
    Insira `viewtinet`.
-   **Your server’s name (Nome do seu servidor):**<br />
    Insira o nome de host desejado. Este nome de host é como o servidor se identificará em sua rede.
-   **Pick a username (Escolha um nome de usuário):**<br />
    Insira `viewtinet`. _(Este nome de usuário é obrigatório.)_
-   **Choose a password (Escolha uma senha):**<br />
    Insira uma senha forte e segura, seguindo as diretrizes de segurança da sua organização.
-   **Confirm your password (Confirme sua senha):**<br />
    Reinsira a senha para confirmar.

Certifique-se de que todos os campos estejam preenchidos corretamente, conforme mostrado no exemplo abaixo:

<br />

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/hFmxz31pTGJmrTg53sRY.png"></figure>

Uma vez que os campos estiverem preenchidos, selecione `[Done]` para prosseguir com a instalação.

---

**Importante:**

-   Não se desvie do uso de `viewtinet` como o nome de usuário do sistema, pois isso é necessário para o funcionamento correto da plataforma.
-   Certifique-se de que a senha que você definir cumpra as políticas de senha da sua organização.

Prossiga para os próximos capítulos após a conclusão da configuração do perfil.

---

<br />