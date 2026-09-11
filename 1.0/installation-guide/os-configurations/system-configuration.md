---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Configuração do Sistema'
id: GG6-I8VJ-HKN-FYJ
slug: system-configuration
isVisible: true
lastUpdated: '2025-10-14 09:45:50'
---
# **<span align="center">Inicialização do Sistema</span>**

<br />
Este capítulo descreve as etapas essenciais necessárias para configurar o perfil do sistema, o serviço SSH e os serviços de sincronização de horário. Essas configurações devem ser concluídas antes de prosseguir com a instalação do Viewtinet.<br />
Configuração do Perfil de Usuário

Todos os módulos, contêineres e serviços do Viewtinet são executados sob o usuário `viewtinet`. Este usuário deve ser criado durante o processo de instalação do sistema operacional.

### Configuração do Perfil Durante a Instalação

Na tela **Profile setup** (Configuração de perfil), insira os seguintes detalhes:

-   **Your name (Seu nome):** `viewtinet`
-   **Your server’s name (Nome do seu servidor):** Qualquer nome de host da sua escolha (ex: `my_viewtilog`)
-   **Pick a username (Escolha um nome de usuário):** `viewtinet`
-   **Choose a password (Escolha uma senha):** Defina uma senha segura
-   **Confirm your password (Confirme sua senha):** Reinsira a mesma senha

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/qRQJX723KTkRI4WS2odl.png"></figure>

Clique em `[Done]` para continuar.

> ⚠️ Não altere o nome de usuário. Ele deve ser `viewtinet` para que o sistema funcione corretamente.

---

## **Configuração do SSH**

Para habilitar o gerenciamento remoto seguro, é obrigatório instalar e habilitar o **OpenSSH Server**.

Na tela **SSH Setup**:

-   Marque a opção: `[X] Install OpenSSH server`
-   Deixe a opção de importar identidade (import identity) como `No`
-   Certifique-se de que: `[X] Allow password authentication over SSH` esteja marcado

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/Ud68BjEZe1OzSldgxJeA.png"></figure>

Clique em `[Done]` para prosseguir.

Pacotes Opcionais

Se o instalador apresentar uma tela para selecionar pacotes adicionais (ex: "Featured Server Snaps"):

-   **Não selecione nenhum pacote**.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/V0OGHxgoBgQn5JAxh0Xl.png"></figure>

<br />

-   Basta clicar em `[Done]` para continuar o processo de instalação.

> ❗A instalação de pacotes adicionais neste momento não é recomendada e pode causar conflitos com os módulos do Viewtinet.

---

## **Configuração do NTP**

A sincronização de horário correta é essencial. Configure o sistema para usar um servidor NTP da seguinte forma:

### **Instalar o Serviço NTP**

```bash
sudo apt-get install ntp
```

### **Editar o Arquivo de Configuração do NTP**

```bash
sudo vi /etc/ntp.conf
```

Se o cliente fornecer servidores NTP, adicione-os abaixo da seção:

```bash
# Specify one or more NTP servers
```

Caso contrário, use servidores NTP públicos mais próximos à sua localização: [https://support.ntp.org/bin/view/Servers/NTPPoolServers](https://support.ntp.org/bin/view/Servers/NTPPoolServers)

<br />

### **Reiniciar o Serviço NTP**

```bash
sudo service ntp restart
```

### **Verificar o Status do NTP**

```bash
sudo service ntp status
```

### **Verificar o Status e a Sincronização**

```bash
sudo systemctl status systemd-timesyncd
timedatectl
```

Saída esperada:

```bash
System clock synchronized: yes
NTP service: active
```

Assim que todas as etapas deste capítulo forem concluídas, o sistema operacional estará configurado corretamente para prosseguir com a instalação do Viewtinet. Continue com as etapas descritas na documentação de Instalação do Pacote (Bundle Installation).

<br />