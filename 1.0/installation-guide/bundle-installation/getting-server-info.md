---
reusableId: 73
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Obtendo informações do servidor'
id: I7G-VSW8-J9P-8HE
slug: getting-server-info
isVisible: true
lastUpdated: '2025-10-15 09:34:18'
---
# **<span align="center">Obtendo as Informações do Servidor</span>**

Para emitir uma licença válida, o Viewtinet requer um identificador de hardware único específico para sua máquina. Esse identificador exclusivo garante que sua instalação do Viewtinet esteja vinculada de forma segura ao seu ambiente designado (seja um appliance físico, máquina virtual ou servidor COTS).

Esse identificador é gerado automaticamente durante as etapas anteriores e armazenado no seguinte caminho de arquivo no seu servidor:
`/opt/vn/viewtimanager/var/server-info.txt`

### **Como Obter Sua Licença**

1. **Baixe o Arquivo Identificador:** Use qualquer cliente SCP (como WinSCP para Windows, ou o comando nativo `scp` no Linux/macOS) para conectar-se ao seu servidor e baixar o arquivo `server-info.txt` para seu computador local.
2. **Envie para o Viewtinet:** Anexe o arquivo baixado em um e-mail e envie para o seu representante ou engenheiro de suporte Viewtinet designado.
3. **Receba Sua Licença:** Após processar seu identificador único, a equipe Viewtinet responderá com seu arquivo de licença oficial (no formato `.key`), que você usará nas etapas seguintes.

<br />

<br />

<br />
