---
reusableId: 68
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Configuração do Sistema'
id: GG6-I8VJ-HKN-FYJ
slug: system-configuration
isVisible: true
lastUpdated: '2025-10-14 09:45:50'
---
# **<span align="center">Inicialização do Sistema</span>**

<br />
Este capítulo descreve as etapas essenciais para configurar o perfil do sistema, o serviço SSH e os serviços de sincronização de tempo. Essas configurações devem ser concluídas antes de prosseguir com a instalação do Viewtinet.<br />
Configuração do Perfil de Usuário

Todos os módulos, contêineres e serviços do Viewtinet são executados sob o usuário `viewtinet`. Este usuário deve ser criado durante o processo de instalação do sistema operacional.

### Configuração de Perfil Durante a Instalação

Na tela de **Configuração de Perfil**, insira os seguintes detalhes:

-   **Seu nome:** `viewtinet`
-   **Nome do seu servidor:** Qualquer hostname de sua escolha (ex.: `my_viewtilog`)
-   **Escolha um nome de usuário:** `viewtinet`
-   **Escolha uma senha:** Defina uma senha segura
-   **Confirme sua senha:** Re-insira a mesma senha

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/qRQJX723KTkRI4WS2odl.png"></figure>

Clique em `[Concluído]` para continuar.

> ⚠️ Não altere o nome de usuário. Deve ser `viewtinet` para o sistema funcionar corretamente.

---

## **Configuração do SSH**

Para habilitar o gerenciamento remoto seguro, é obrigatório instalar e habilitar o **Servidor OpenSSH**.

Na tela de **Configuração do SSH**:

-   Marque a opção: `[X] Instalar servidor OpenSSH`
-   Deixe a opção de importar identidade como `Não`
-   Certifique-se de que: `[X] Permitir autenticação por senha via SSH` esteja marcado

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/Ud68BjEZe1OzSldgxJeA.png"></figure>

Clique em `[Concluído]` para prosseguir.

Pacotes Opcionais

Se o instalador apresentar uma tela para selecionar pacotes adicionais (ex.: "Snaps de Servidor em Destaque"):

-   **Não selecione nenhum pacote**.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/V0OGHxgoBgQn5JAxh0Xl.png"></figure>

<br />

-   Simplesmente clique em `[Concluído]` para continuar o processo de instalação.

> ❗ A instalação de pacotes adicionais neste ponto não é recomendada e pode causar conflitos com os módulos do Viewtinet.

---

## **Configuração NTP**

A sincronização correta do tempo é essencial. Configure o sistema para usar um servidor NTP da seguinte forma:

### **Instalar o Serviço NTP**

```bash
sudo apt-get install ntp
```

### **Editar o Arquivo de Configuração NTP**

```bash
sudo vi /etc/ntp.conf
```

Se o cliente fornecer servidores NTP, adicione-os abaixo da seção:

```bash
# Specify one or more NTP servers
```

Caso contrário, use servidores NTP públicos mais próximos da sua localização: [https://support.ntp.org/bin/view/Servers/NTPPoolServers](https://support.ntp.org/bin/view/Servers/NTPPoolServers)

<br />

### **Reiniciar o Serviço NTP**

```bash
sudo service ntp restart
```

### **Verificar o Status do NTP**

```bash
sudo service ntp status
```

### **Verificar Status e Sincronização**

```bash
sudo systemctl status systemd-timesyncd
timedatectl
```

Saída esperada:

```bash
System clock synchronized: yes
NTP service: active
```

Após concluir todas as etapas deste capítulo, o sistema operacional está corretamente configurado para prosseguir com a instalação do Viewtinet. Continue com as etapas descritas na documentação de Instalação pelo Bundle.

<br />
