---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'SCP Producer'
id: SCP-PRD-FL1-TR4
slug: scp-producer
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 16:31:00'
---
# **<span align="center">Produtor SCP (SCP Producer)</span>**

<br />

O **SCP Producer** permite transferir arquivos de forma segura do servidor Viewtinet para um host remoto usando o **SCP (Secure Copy Protocol)** sobre SSH. Em vez de exportar linhas individuais de grade como outros produtores, o Produtor SCP trabalha no **nível de arquivo**, pegando arquivos de um diretório local e entregando-os a um caminho especificado no servidor remoto.

<br />

---

## **Pré-requisito: Conector de Lista de Arquivos (File List Connector)**

<div class="sd-callout" data-callout-type="warning"><strong>Importante:</strong> O Produtor SCP <strong>não</strong> funciona de forma independente. Ele requer que o <strong>File List Connector</strong> seja configurado na <strong>etapa Extract</strong> do mesmo pipeline.<br /><br />O File List Connector é responsável por coletar arquivos de um diretório <code>to-collect</code> (a coletar) e movê-los para um diretório <code>to-send</code> (a enviar). O Produtor SCP então pega os arquivos do diretório <code>to-send</code> e os transfere para o destino remoto via SCP.<br /><br />Por favor, consulte a documentação do <strong>File List Connector</strong> na seção <strong>Extract</strong> para ver os detalhes completos de sua configuração.</div>

<br />

---

## **Parâmetros de Configuração**

Depois de selecionar `SCP Producer` no menu suspenso de Tipo de Produtor, os seguintes parâmetros de conexão e transferência ficam disponíveis:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/scp-producer-config.png" align="center"></figure>

<br />

-   **Host:** O endereço IP ou nome do host do servidor remoto onde os arquivos serão entregues (ex., `10.30.23.10`).
-   **Destination path** (Caminho de destino): O caminho do diretório absoluto no servidor remoto onde os arquivos serão colocados (ex., `/home/remote_directory`).
-   **Port** (Porta): A porta SSH no servidor remoto. O padrão padrão é `22`.
-   **Username** (Nome de usuário): A conta de usuário SSH usada para autenticar a conexão no host remoto (ex., `remote_user`).
-   **Password** (Senha): A senha para a conta de usuário SSH especificada.
-   **Keep Files** (Manter Arquivos): Quando esta caixa de seleção está **desmarcada** (comportamento padrão), o Produtor SCP **excluirá os arquivos locais** do diretório `to-send` depois que eles tiverem sido transferidos com sucesso para o servidor remoto. Se estiver **marcada**, as cópias locais dos arquivos serão preservadas mesmo após a conclusão da transferência.

<br />

> [!WARNING] **Verificação de Conectividade**<br />
> O Produtor SCP depende do **protocolo SSH** para estabelecer uma conexão segura com o servidor remoto. Antes de habilitar este produtor, é **responsabilidade do administrador** garantir que:<br />
> - O host remoto está **acessível** a partir do servidor Viewtinet.<br />
> - A **porta SSH** configurada (padrão `22`) está **aberta e acessível** por quaisquer firewalls intermediários ou políticas de rede.<br />
> - As **credenciais** fornecidas (nome de usuário e senha) são válidas e têm **permissões de gravação** no caminho de destino.<br /><br />
> É altamente recomendável realizar um teste manual de conexão SCP ou SSH a partir da linha de comando do servidor Viewtinet antes de ativar este produtor para confirmar que a transferência será bem-sucedida.

<br />
