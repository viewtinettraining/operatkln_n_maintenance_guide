---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Entrar'
id: HLG-ZK7U-1XT-GW7
slug: login
isVisible: true
isSearchable: true
lastUpdated: '2026-09-10 19:54:19'
---
# **<span align="center">Acessando a Plataforma Viewtinet</span>**

<br />
<span align="justify">O acesso à plataforma Viewtinet é gerenciado por meio do módulo Viewtiauth, que fornece autenticação centralizada para todos os componentes. Os usuários devem se autenticar por meio de uma página de login antes de obter acesso ao Viewtimanager, Viewtisight ou outros módulos do sistema.</span>

<br />

### **🌐 URLs de Acesso**

O módulo Viewtiauth escuta em duas portas diferentes, dependendo do modo de segurança utilizado:

<table><tbody><tr><th><p>Protocolo</p></th><th><p>Formato da URL</p></th><th><p>Descrição</p></th></tr><tr><td><p>HTTP</p></td><td><p><code>http://&lt;platform-ip&gt;:4200</code></p></td><td><p>Conexão não segura (não recomendada para produção)</p></td></tr><tr><td><p>HTTPS</p></td><td><p><code>https://&lt;platform-ip&gt;:4201</code></p></td><td><p>Conexão segura com criptografia (recomendada)</p></td></tr></tbody></table>

> ⚠️ **Importante:**<br />
> Embora tanto o HTTP quanto o HTTPS sejam suportados por padrão, é altamente recomendável acessar a plataforma usando **HTTPS (porta 4201)**. Isso garante que as credenciais e os dados da sessão sejam criptografados durante a transmissão.<br />
> A plataforma pode exibir um aviso no navegador se forem usados **certificados autoassinados**. Para instalar certificados confiáveis, entre em contato com o **Helpdesk da Viewtinet**.

---

### 🔑 Formulário de Login

Uma vez conectado à URL de login, o usuário visualizará um formulário de login solicitando:

-   **Username** (Nome de usuário)
-   **Password** (Senha)
-   **Language selection** (Seleção de idioma no menu suspenso inferior)

Clique no botão **Login** para enviar suas credenciais para validação.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/VCW02tM70cpSzc0AXJl3.png" align="center"></figure>

---

### 🔄 Fluxo de Autenticação

1.  As credenciais são validadas pelo módulo **Viewtiauth**.
2.  Após o login bem-sucedido, o usuário é redirecionado para a tela do **Seletor de Aplicativos** (App Selector).

---

### 🧭 Seletor de Aplicativos (App Selector)

Após o login, o App Selector exibirá os módulos disponíveis que o usuário tem permissão para acessar:

-   📊 **Viewtisight** – Visualização e painéis (dashboards).
-   ⚙️ **Viewtimanager** – Administração do sistema e dos módulos.

Clique no módulo desejado para entrar em sua interface.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/u8RnjfTOSw9cb8OXCY3M.png" align="center"></figure>

<br />

> 🔐 **Nota**: Os direitos de acesso são gerenciados dentro da plataforma Viewtinet. Se um usuário não tiver permissão para acessar um módulo, ele poderá não aparecer no seletor.

---

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/EH3vMbAvcD9s2bNsJD5n.png" align="center"></figure>

<br />

### **🔁 Acesso Direto aos Módulos**

Também é possível acessar os módulos diretamente por meio de suas portas dedicadas:

<table><tbody><tr><th><p>Módulo</p></th><th><p>Protocolo</p></th><th><p>Formato da URL</p></th></tr><tr><td><p>Viewtimanager</p></td><td><p>HTTP</p></td><td><p><code>http://&lt;platform-ip&gt;:5000</code></p></td></tr><tr><td><p>Viewtimanager</p></td><td><p>HTTPS</p></td><td><p><code>https://&lt;platform-ip&gt;:5001</code></p></td></tr></tbody></table>

> 📌 **Nota**:<br />
> Ao acessar essas portas diretamente, se uma sessão válida ainda não existir no navegador, o usuário será redirecionado automaticamente para a página de login do **Viewtiauth** para se autenticar antes de receber acesso ao módulo solicitado.

Isso permite salvar o acesso aos módulos nos favoritos ou via scripts, preservando o gerenciamento centralizado de sessão e autenticação.

<br />

### ✅ Resumo

-   A autenticação é centralizada via **Viewtiauth**, acessível em:
    
    -   `http://&lt;platform-ip&gt;:4200` (HTTP – não seguro)
    -   `https://&lt;platform-ip&gt;:4201` (HTTPS – seguro)
-   O login é obrigatório para acessar o **Viewtimanager** ou o **Viewtisight**.
-   Após o login bem-sucedido, o **Seletor de Aplicativos** aparecerá.
-   Sempre use HTTPS em ambientes de produção para garantir o acesso seguro.

<br />
<br />
