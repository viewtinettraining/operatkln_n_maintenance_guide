---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Readme First Updating '
id: DDC-YZMU-EHR-VBH
slug: readme-first-updating
isVisible: true
lastUpdated: '2025-10-15 16:13:05'
---
# **<span align="center">Atualizando o Viewtinet</span>**

<span align="justify">Neste capítulo, abordaremos como atualizar toda a sua plataforma Viewtinet — ou módulos individuais — usando apenas a interface de linha de comando (CLI). As atualizações são distribuídas como pacotes ZIP e devem ser carregadas em suas instâncias do Ubuntu Server (appliances físicos ou VMs) antes de aplicá-las.</span>

### Pré-requisitos

Antes de começar, certifique-se de ter:

-   **Acesso SSH** ao(s) servidor(es) de destino, com regras de firewall permitindo a porta TCP **22** a partir da sua estação de trabalho.
-   Um terminal com capacidade para CLI na sua máquina local (Terminal Linux/macOS, Windows PowerShell, etc.).
-   Um dos seguintes clientes SCP/SFTP instalados para upload do pacote:
    
    -   **WinSCP**
    -   **FileZilla**
    -   **PuTTY PSCP**
    -   `scp` do **OpenSSH** (nativo no Linux/macOS; disponível no Windows 10+)

> **Nota:** Tanto o pacote de atualização da plataforma completa quanto os arquivos ZIP específicos de módulos são fornecidos diretamente pelos engenheiros da Viewtinet. No momento da redação deste documento, não há um repositório público para esses pacotes.

As seções subsequentes guiarão você pelos comandos da CLI para aplicar esses pacotes, verificar as versões e confirmar uma atualização bem-sucedida.