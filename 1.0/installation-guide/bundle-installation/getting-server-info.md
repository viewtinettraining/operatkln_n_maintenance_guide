---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Getting server info'
id: I7G-VSW8-J9P-8HE
slug: getting-server-info
isVisible: true
lastUpdated: '2025-10-15 09:34:18'
---
# **<span align="center">Obtendo as Informações do Servidor</span>**

Para emitir uma licença válida, o Viewtinet exige um identificador de hardware único específico da sua máquina. Essa impressão digital exclusiva garante que sua instalação do Viewtinet esteja vinculada de forma segura ao seu ambiente designado (seja um appliance físico, máquina virtual ou servidor COTS). 

Este identificador é gerado automaticamente durante as etapas anteriores e é armazenado no seguinte caminho de arquivo no seu servidor:
`/opt/vn/viewtimanager/var/server-info.txt`

### **Como Obter Sua Licença**

1. **Baixe o Arquivo Identificador:** Use qualquer cliente SCP (como o WinSCP para Windows ou o comando nativo `scp` no Linux/macOS) para se conectar ao seu servidor e baixar o arquivo `server-info.txt` para o seu computador local.
2. **Envie para a Viewtinet:** Anexe o arquivo baixado em um e-mail e envie-o ao seu representante ou engenheiro de suporte da Viewtinet designado.
3. **Receba Sua Licença:** Após processar seu identificador único, a equipe da Viewtinet responderá com o arquivo oficial de licença (no formato `.key`), que você usará nas próximas etapas.

<br />

<br />

<br />