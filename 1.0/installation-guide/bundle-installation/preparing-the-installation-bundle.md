---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Preparando o Pacote de Instalação'
id: LQB-DJ6N-7GW-42C
slug: preparing-the-installation-bundle
isVisible: true
isSearchable: true
lastUpdated: '2026-03-10 15:37:45'
---
# **<span align="center">Preparando o Pacote de Instalação</span>**

<br />
Este capítulo descreve as etapas necessárias para baixar, enviar e extrair o pacote de instalação do Viewtinet no servidor designado (appliance, VM ou hardware COTS).

<br />

## **Baixando o Pacote**

O pacote de instalação do Viewtinet é fornecido como um arquivo `.tgz` compactado. Um representante de vendas ou engenheiro de suporte da Viewtinet fornecerá um link de download para recuperar o pacote.

Além disso, você deve receber o seguinte do seu contato na Viewtinet:

-   O arquivo de pacote oficial **.tgz**.
-   Uma **frase secreta (passphrase)**, que é obrigatória para o processo de instalação.

A convenção de nomenclatura do pacote segue esta estrutura: `bundle-6.3.5-ubuntu24.04-rXXXX-YYYYMMDDHHMMSS.tgz`.

-   O prefixo `bundle-6.3.5-ubuntu24.04` permanece constante para esta versão.
-   Os caracteres subsequentes representam a revisão de compilação específica e o carimbo de data/hora de geração.

Certifique-se de que o arquivo seja baixado e armazenado localmente em sua máquina antes de prosseguir para a próxima etapa.

---

## **Enviando o Pacote**

Assim que o pacote for baixado, ele deve ser enviado (upload) para o servidor onde o Viewtinet será instalado. É recomendável enviar o arquivo para o diretório `/home/viewtinet`.

<br />

### **Usando SCP a partir do Terminal Linux**

Se você estiver usando um sistema baseado em Linux, abra um terminal e execute (substituindo o nome do arquivo pela sua compilação específica):

```bash
scp bundle-6.3.5-ubuntu24.04-r5767-20260302080607.tgz viewtinet@<SERVER_IP>:/home/viewtinet
```

> **Nota:** Substitua `&lt;SERVER_IP&gt;` pelo endereço IP real do seu servidor em todos os exemplos.

<br />

### **Usando WinSCP (Windows)**

Para ambientes Windows, use um cliente SCP com interface gráfica como o **WinSCP**:

1.  Abra o **WinSCP**.
2.  Insira os seguintes detalhes de conexão:
    
    -   **Host name (Nome do host):** Endereço IP do seu servidor
    -   **User name (Nome de usuário):** `viewtinet`
    -   **Password (Senha):** Senha configurada durante a configuração do sistema
3.  Navegue em sua máquina local até a pasta onde o arquivo `.tgz` está localizado.
4.  Envie o arquivo para o diretório `/home/viewtinet` no servidor.

---

## **Conexão SSH**

Se você não estiver trabalhando diretamente no appliance, máquina virtual ou servidor COTS, você precisará se conectar remotamente via SSH.

Dependendo do seu sistema operacional, você pode se conectar usando o terminal integrado ou um aplicativo de terceiros:

### Usando a Linha de Comando (Windows 10+, macOS, Linux)

A maioria dos sistemas operacionais modernos possui um cliente SSH embutido. Você pode se conectar facilmente usando o terminal do seu sistema (Prompt de Comando, PowerShell ou Terminal padrão do Linux/macOS):

1.  Abra seu terminal.
2.  Execute o seguinte comando, substituindo `<SERVER_IP>` pelo endereço IP real do seu servidor:
    
    ```bash
    ssh viewtinet@<SERVER_IP>
    ```

3.  Quando solicitado, insira a senha para o usuário `viewtinet`.

### Usando Clientes com Interface Gráfica

Se você prefere uma interface gráfica ou está usando uma versão mais antiga do Windows, pode usar um cliente SSH dedicado, como **PuTTY** ou **MobaXterm**:

1.  Abra seu cliente SSH preferido.
2.  No campo **Host Name**, insira o endereço IP do seu servidor.
3.  Inicie a conexão e faça login usando as credenciais do usuário `viewtinet`.

Após fazer o login com sucesso, você terá acesso à interface de linha de comando do servidor para continuar com as etapas de instalação.

---

## **Extraindo o Pacote**

O pacote do Viewtinet deve ser extraído antes da instalação.

### **Navegando e Extraindo**

Navegue até o diretório onde o pacote de instalação foi enviado. Por padrão, isso é:

```bash
cd /home/viewtinet
```

Em seguida, execute o seguinte comando para extrair o conteúdo do arquivo `.tgz` (substitua pelo seu nome de arquivo específico):

```bash
tar -xvf bundle-6.3.5-ubuntu24.04-r5767-20260302080607.tgz
```

Após a extração, um novo diretório chamado `bundle` será criado. Todas as etapas de instalação subsequentes serão realizadas a partir desse diretório.

Após descompactar o pacote, você verá uma saída com os seguintes arquivos e scripts:

```bash
decrypt.sh
deploy.sh
software-bundle-6.3.5-r5767.tgz.gpg
viewtinet-pub.asc
```

<div class="sd-callout" data-callout-type="info">Tenha em mãos a <strong>frase secreta (passphrase)</strong> fornecida pela Viewtinet, pois ela será necessária durante a execução dos scripts de instalação nas etapas seguintes.</div>

<br />