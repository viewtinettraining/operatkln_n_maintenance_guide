---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Installation step1 '
id: SM3-711J-KFE-QS7
slug: installation-step1
isVisible: true
isSearchable: true
lastUpdated: '2026-03-10 15:51:34'
---
# <span align="center">Passo 1 da Instalação</span>

<br />

<div class="sd-callout" data-callout-type="alert">O acesso à internet é obrigatório durante o processo de instalação, pois todas as bibliotecas e ferramentas necessárias para a execução do Viewtinet serão instaladas</div>

<div class="sd-callout" data-callout-type="info">A instalação é realizada em 3 etapas: implantação, instalação de dependências, carregamento de imagens e configuração</div>

O primeiro passo é executar o script de implantação:

```bash
./deploy.sh
```

Após a execução, você verá os seguintes prompts e o progresso:

```bash
viewtinet@dante:~$ ./deploy.sh
Uncompressing and deploying software... This may take a while. Please wait.
Please write the bundle passphrase:
```

<div class="sd-callout" data-callout-type="info">Neste momento, insira a <strong>frase secreta (passphrase)</strong> que foi enviada junto com o seu pacote (bundle).</div>

Após inserir a frase secreta, o sistema prosseguirá com a implantação. Ao final do processo, você verá uma saída semelhante à mostrada abaixo:

```bash
Deploying current software
Moving deb file /home/viewtinet/_build/viewtinet-builder_6.3.5.5767_all.deb to /opt/vn/software/viewtinet-builder_6.3.5.5767_all.deb
Moving module dependencies to /opt/vn/software/dependencies
Moving module dhyana to /opt/vn/software/dhyana
Moving module license-checker to /opt/vn/software/license-checker
Moving module release-notes to /opt/vn/software/release-notes
Moving module third-party to /opt/vn/software/third-party
Moving module viewtiauth to /opt/vn/software/viewtiauth
Moving module viewticore to /opt/vn/software/viewticore
Moving module viewtimanager to /opt/vn/software/viewtimanager
Moving module viewtimon to /opt/vn/software/viewtimon
Moving module viewtisight to /opt/vn/software/viewtisight
Installing deb file
Selecting previously unselected package viewtinet-builder.
(Reading database ... 94807 files and directories currently installed.)
Preparing to unpack .../viewtinet-builder_6.3.5.5767_all.deb ...
Unpacking viewtinet-builder (6.3.5.5767) ...
Setting up viewtinet-builder (6.3.5.5767) ...
INFO: Generating application-level RSA key pair... writing RSA key
viewtinet@dante:~$
```

<br />