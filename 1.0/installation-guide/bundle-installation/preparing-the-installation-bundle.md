---
reusableId: 69
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Preparando o Bundle de Instalação'
id: LQB-DJ6N-7GW-42C
slug: preparing-the-installation-bundle
isVisible: true
isSearchable: true
lastUpdated: '2026-03-10 15:37:45'
---
# **<span align="center">Preparando o Bundle de Instalação</span>**

<br />
Este capítulo descreve as etapas necessárias para baixar, enviar e extrair o bundle de instalação do Viewtinet no servidor designado (appliance, VM ou hardware COTS).

<br />

## **Baixando o Bundle**

O pacote de instalação do Viewtinet é entregue como um arquivo `.tgz` comprimido. Um representante de vendas ou engenheiro de suporte do Viewtinet fornecerá um link para baixar o bundle.

Além disso, você deve receber o seguinte do seu contato Viewtinet:

-   O arquivo oficial de bundle **.tgz**.
-   Uma **senha (passphrase)**, que é obrigatória para o processo de instalação.

A convenção de nomenclatura do bundle segue esta estrutura: `bundle-6.3.5-ubuntu24.04-rXXXX-YYYYMMDDHHMMSS.tgz`.

-   O prefixo `bundle-6.3.5-ubuntu24.04` permanece constante para esta versão.
-   Os caracteres subsequentes representam a revisão específica do build e o timestamp de geração.

Certifique-se de que o arquivo foi baixado e armazenado localmente em sua máquina antes de prosseguir para a próxima etapa.

---

## **Enviando o Bundle ao Servidor**

Assim que o bundle for baixado, ele deve ser enviado para o servidor onde o Viewtinet será instalado. Recomenda-se enviar o arquivo para o diretório `/home/viewtinet`.

<br />

### **Usando SCP pelo Terminal Linux**

Se estiver usando um sistema baseado em Linux, abra um terminal e execute (substituindo o nome do arquivo pelo seu build específico):

```bash
scp bundle-6.3.5-ubuntu24.04-r5767-20260302080607.tgz viewtinet@<SERVER_IP>:/home/viewtinet
```

> **Nota:** Substitua `&lt;SERVER_IP&gt;` pelo endereço IP real do seu servidor em todos os exemplos.

<br />

### **Usando WinSCP (Windows)**

Para ambientes Windows, use um cliente SCP com interface gráfica como o **WinSCP**:

1.  Abra o **WinSCP**.
2.  Insira os seguintes detalhes de conexão:
    
    -   **Nome do host:** Endereço IP do seu servidor
    -   **Nome de usuário:** `viewtinet`
    -   **Senha:** Senha configurada durante a configuração do sistema
3.  Navegue em sua máquina local até a pasta onde o arquivo `.tgz` está localizado.
4.  Envie o arquivo para o diretório `/home/viewtinet` no servidor.

---

## **Conexão SSH**

Se você não estiver trabalhando diretamente no appliance, máquina virtual ou servidor COTS, deverá conectar-se remotamente via SSH.

Dependendo do seu sistema operacional, você pode se conectar usando o terminal integrado ou um aplicativo de terceiros:

### Usando a Linha de Comando (Windows 10+, macOS, Linux)

A maioria dos sistemas operacionais modernos vem com um cliente SSH integrado. Você pode se conectar facilmente usando o terminal do sistema (Prompt de Comando, PowerShell ou terminal Linux/macOS padrão):

1.  Abra seu terminal.
2.  Execute o seguinte comando, substituindo `<SERVER_IP>` pelo endereço IP real do seu servidor:
    
    ```bash
    ssh viewtinet@<SERVER_IP>
    ```

3.  Quando solicitado, insira a senha do usuário `viewtinet`.

### Usando Clientes GUI

Se preferir uma interface gráfica ou estiver usando uma versão mais antiga do Windows, você pode usar um cliente SSH dedicado como **PuTTY** ou **MobaXterm**:

1.  Abra seu cliente SSH preferido.
2.  No campo **Nome do Host**, insira o endereço IP do seu servidor.
3.  Inicie a conexão e faça login usando as credenciais do usuário `viewtinet`.

Após o login bem-sucedido, você terá acesso à interface de linha de comando do servidor para continuar com as etapas de instalação.

---

## **Extraindo o Bundle**

O bundle do Viewtinet deve ser extraído antes da instalação.

### **Navegando e Extraindo**

Navegue até o diretório onde o bundle de instalação foi enviado. Por padrão, este é:

```bash
cd /home/viewtinet
```

Em seguida, execute o seguinte comando para extrair o conteúdo do arquivo `.tgz` (substitua pelo seu nome de arquivo específico):

```bash
tar -xvf bundle-6.3.5-ubuntu24.04-r5767-20260302080607.tgz
```

Após a extração, um novo diretório chamado `bundle` será criado. Todas as etapas subsequentes de instalação serão realizadas dentro deste diretório.

Após descomprimir o bundle, você verá uma saída com os seguintes arquivos e scripts:

```bash
decrypt.sh
deploy.sh
software-bundle-6.3.5-r5767.tgz.gpg
viewtinet-pub.asc
```

<div class="sd-callout" data-callout-type="info">Mantenha a <strong>senha (passphrase)</strong> fornecida pelo Viewtinet em mãos, pois será necessária durante a execução dos scripts de instalação nas etapas seguintes.</div>

<br />
