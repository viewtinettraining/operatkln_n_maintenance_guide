---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Atualizando o Pacote (Bundle)'
id: XY9-HS55-0VV-2F9
slug: updating-bundle
isVisible: true
lastUpdated: '2025-10-15 16:20:46'
---
# **<span align="center">Atualizando Todos os Módulos de Uma Vez</span>**

Esta seção orienta você sobre como aplicar um pacote de atualização de plataforma completa (`artifacts.zip`) a todos os módulos do Viewtinet em uma única operação via CLI.

> **Nota:** Tanto o nome do arquivo do pacote quanto os números de versão mostrados aqui são exemplos; os nomes de arquivos e versões reais irão variar. Os pacotes de atualização são fornecidos diretamente pelos engenheiros da Viewtinet (nenhum repositório público está disponível no momento).

---

## **1\. Faça o Upload do Pacote de Atualização**

Use o seu cliente SCP/SFTP preferido para copiar o pacote ZIP para o servidor. Por exemplo, com o `scp` do OpenSSH:

```bash

scp artifacts.zip viewtinet@your-server:/home/viewtinet/

```

Ou com PuTTY PSCP:

```bash
pscp artifacts.zip viewtinet@your-server:/home/viewtinet/
```

## **2\. Acesse o Servidor via SSH**

Conecte-se ao servidor usando um cliente SSH (ssh do Linux/macOS, Windows PuTTY, etc.):

```bash
ssh viewtinet@your-server
```

## **3\. Descompacte o Pacote**

Navegue até o diretório onde você fez o upload de artifacts.zip e descompacte-o:

```bash
cd /home/viewtinet
unzip artifacts.zip
```

Você deverá ver uma saída semelhante a:

```bash
Archive:  artifacts.zip
  creating: bundle/
 inflating: bundle/deploy
 inflating: bundle/deploy.sh
 inflating: bundle/public_key.pem
 inflating: bundle/signature
 inflating: bundle/software-bundle-6.3.5-r3243.tgz.bin
```

## **4\. Implante o Novo Software**

Execute o script de implantação para desempacotar e instalar tudo em /opt/vn/software:

```bash
./bundle/deploy.sh
```

Exemplo de saída (truncada):

```bash
Uncompressing and deploying software... This may take a while.
Uncompressing software bundle /home/viewtinet/bundle/software-bundle-6.3.5-r3243.tgz
Deploying software
Backing up prior version to folder /opt/vn/software_bk_1745401625. Remove it manually if there is no need to keep it.
Backing up dhyana to /opt/vn/software_bk_1745401625/dhyana
...
Moving module viewtimon to /opt/vn/software/viewtimon
Installing deb file
(Reading database ... 112870 files and directories currently installed.)
Preparing to unpack .../viewtinet-builder_6.3.3243_all.deb ...
Unpacking viewtinet-builder (6.3.3243) over (6.3.3243) ...
Setting up viewtinet-builder (6.3.3243) ...
 Please wait
Deployment complete.
```

**Aviso:** Os sufixos numéricos (ex.: 6.3.5-r3243, 1745401625) diferirão com base na versão do pacote e no carimbo de data/hora.

## **5\. Carregue as Imagens Docker**

Por fim, atualize e carregue todas as imagens de contêiner para o software recém-implantado:

```bash
/opt/vn/viewtinet-builder/install-packages.sh --software-directory /opt/vn/software
```

Esta etapa baixa e carrega as imagens Docker para cada módulo. Dependendo da CPU, memória e largura de banda de rede do seu servidor, isso pode levar vários minutos.

> **Nota:** Após carregar novas imagens de software, o sistema aciona automaticamente uma reinicialização **apenas** para o módulo `viewtimanager`.

Existem duas maneiras de carregar versões de módulos atualizadas:

---

#### 1\. Reinício completo da solução

```bash
/opt/vn/viewtinet-builder/scripts/stop-all.sh
# wait for all modules to stop
/opt/vn/viewtinet-builder/scripts/start-all.sh
```

> ⚠️ Esta abordagem é a mais demorada e causará uma interrupção completa da coleta de dados, ingestão e visualização em toda a plataforma.

2.  **Reinício módulo por módulo** (recomendado para menor tempo de inatividade)<br />
    Use os scripts individuais de módulo descritos no capítulo _[Operating Viewtinet Containers via Scripts](http:#?target=20U-C19U-8N7-KWB)_. Embora isso ainda incorra em breve indisponibilidade por módulo, o impacto total é muito menor que um reinício completo.

<br />