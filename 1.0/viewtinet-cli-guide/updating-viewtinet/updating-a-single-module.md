---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Atualizando um Único Módulo'
id: D9M-IWLN-96U-LDX
slug: updating-a-single-module
isVisible: true
lastUpdated: '2025-10-15 16:21:31'
---
# **<span align="center">Atualizando um Único Módulo via CLI</span>**

Esta seção descreve como atualizar apenas um módulo do Viewtinet (por exemplo, `dhyana`) usando a CLI. O pacote de atualização contém apenas os arquivos de imagem Docker para esse módulo.

> **Nota:** Assim como o pacote da plataforma completa, os ZIPs de atualização de módulos são fornecidos por engenheiros da Viewtinet; não há repositório público no momento.

---

## **1\. Faça o Upload do Pacote do Módulo**

Copie o pacote ZIP do módulo para o seu servidor via SCP/SFTP. Por exemplo:

```bash
scp dhyana-artifacts.zip viewtinet@your-server:/home/viewtinet/
```

## **2\. Acesse o Servidor via SSH**

```bash
ssh viewtinet@your-server
```

## **3\. Descompacte em um Diretório Específico do Módulo**

Crie um diretório de preparação chamado software/ descompactando:

```bash
cd /home/viewtinet
unzip dhyana-artifacts.zip
```

Exemplo de saída:

```bash
Archive:  artifacts.zip
  creating: software/dhyana/
 inflating: software/dhyana/images.txt
 inflating: software/dhyana/viewtinet-kafka-6.3.5.tar.gz
 inflating: software/dhyana/viewtinet-viewtinet-dhyana-config-6.3.5.tar.gz
 inflating: software/dhyana/viewtinet-viewtinet-dhyana-dhyana-6.3.5.tar.gz
 inflating: software/dhyana/viewtinet-zookeeper-6.3.5.tar.gz
```

Árvore resultante:

```bash
└── software
    └── dhyana
        ├── images.txt
        ├── viewtinet-kafka-6.3.5.tar.gz
        ├── viewtinet-viewtinet-dhyana-config-6.3.5.tar.gz
        ├── viewtinet-viewtinet-dhyana-dhyana-6.3.5.tar.gz
        └── viewtinet-zookeeper-6.3.5.tar.gz
```

## **4\. Faça Backup do Módulo Existente**

Mova a pasta atual do módulo para fora do caminho:

```bash
mv /opt/vn/software/dhyana/ /opt/vn/software/dhyana_backup
```

**Dica**: Você pode nomear seu diretório de backup com um carimbo de data/hora ou sufixo de versão para identificá-lo, ex.: /opt/vn/software/dhyana\_backup\_$(date +%Y%m%d)}

<br />

## **5\. Implante os Novos Arquivos do Módulo:**

Copie o novo diretório do módulo para o local. A flag -r é necessária para diretórios; -v (verbose) é opcional:

```bash
cp -rv ./software/dhyana/ /opt/vn/software/
```

Exemplo de saída:

```bash
'./software/dhyana/images.txt' -> '/opt/vn/software/dhyana/images.txt'
'./software/dhyana/viewtinet-kafka-6.3.5.tar.gz' -> '/opt/vn/software/dhyana/viewtinet-kafka-6.3.5.tar.gz'
'./software/dhyana/viewtinet-viewtinet-dhyana-config-6.3.5.tar.gz' -> '/opt/vn/software/dhyana/viewtinet-viewtinet-dhyana-config-6.3.5.tar.gz'
'./software/dhyana/viewtinet-viewtinet-dhyana-dhyana-6.3.5.tar.gz' -> '/opt/vn/software/dhyana/viewtinet-viewtinet-dhyana-dhyana-6.3.5.tar.gz'
'./software/dhyana/viewtinet-zookeeper-6.3.5.tar.gz' -> '/opt/vn/software/dhyana/viewtinet-zookeeper-6.3.5.tar.gz'
```

<br />

## **6\. Carregue as Imagens Docker do Módulo**

Use o script install-packages.sh com as flags --software-directory e --module para carregar e instalar as novas imagens de contêiner para o módulo. Substitua pelo nome do módulo:

```bash
/opt/vn/viewtinet-builder/install-packages.sh ---software-directory /opt/vn/software --module dhyana
```

Este comando baixa e carrega os arquivos de imagem Docker para o módulo dhyana. O tempo de execução variará com base na CPU, memória e largura de banda da rede.

⚠️ Após carregar as imagens, lembre-se de reiniciar o módulo usando os scripts descritos em [Operating Viewtinet Containers](http:#?target=20U-C19U-8N7-KWB) via Scripts para aplicar a atualização.<br />