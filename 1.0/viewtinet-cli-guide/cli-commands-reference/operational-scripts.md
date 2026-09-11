---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Operational Scripts'
id: 86R-WT9P-MP0-NDE
slug: operational-scripts
isVisible: true
lastUpdated: '2025-10-15 16:11:57'
---
# **<span align="center">Scripts Operacionais da CLI</span>**

A Viewtinet inclui um conjunto de scripts da CLI de propósito geral que permitem aos administradores realizar operações de rotina e tarefas de manutenção de forma eficiente. Estes scripts estão localizados em:

```
/opt/vn/viewtinet-builder/scripts/
```

Eles são executáveis diretamente pelo usuário `viewtinet` e cobrem uma ampla gama de operações, incluindo iniciar e parar a plataforma completa, exportar/importar backups, realizar limpeza de logs e executar diagnósticos.

---

## **Principais Scripts Operacionais**

#### `start-all.sh`

Inicia todos os módulos na ordem correta.

```bash
/opt/vn/viewtinet-builder/scripts/start-all.sh
```

#### `stop-all.sh`

Para todos os módulos de forma segura e ordenada.

```bash
/opt/vn/viewtinet-builder/scripts/stop-all.sh
```

#### `start-gui.sh`

Inicia apenas os módulos da interface gráfica (GUI).

```bash
/opt/vn/viewtinet-builder/scripts/start-gui.sh
```

#### `stop-gui.sh`

Para apenas os módulos da interface gráfica (GUI).

```bash
/opt/vn/viewtinet-builder/scripts/stop-gui.sh
```

---

## **Scripts Utilitários Adicionais**

<table><tbody><tr><th><p><span align="center">Script</span></p></th><th><p><span align="center">Descrição</span></p></th></tr><tr><td><p><code>get_logs.sh</code></p></td><td><p>Coleta logs de contêineres ativos</p></td></tr><tr><td><p><code>get_node_ip.sh</code></p></td><td><p>Recupera o endereço IP do nó atual</p></td></tr><tr><td><p><code>check_ip.sh</code>, <code>check_vrrp.sh</code></p></td><td><p>Verifica as atribuições de IP e a configuração do VRRP</p></td></tr><tr><td><p><code>init.sh</code></p></td><td><p>Inicializa pastas necessárias e permissões</p></td></tr><tr><td><p><code>update-repo.sh</code></p></td><td><p>Atualiza os metadados do repositório</p></td></tr><tr><td><p><code>uncompress-file.sh</code></p></td><td><p>Extrai arquivos <code>.tar.gz</code> ou <code>.tgz</code></p></td></tr><tr><td><p><code>exec_job.sh</code></p></td><td><p>Executa uma tarefa agendada predefinida</p></td></tr></tbody></table>

---

## **Execução e Permissões**

Todos os scripts neste diretório são pré-configurados para serem executados pelo usuário `viewtinet` e não requerem `sudo`.

```bash
cd /opt/vn/viewtinet-builder/scripts/
./start-all.sh
```

---

## **Scripts Operacionais por Categoria de Tarefa**

<table><tbody><tr><th><p><strong><span align="center">Categoria</span></strong></p></th><th><p><strong><span align="center">Script</span></strong></p></th><th><p><strong><span align="center">Descrição</span></strong></p></th></tr><tr><td><p><strong>Inicialização / Desligamento</strong></p></td><td><p><code>start-all.sh</code>, <code>stop-all.sh</code></p></td><td><p>Inicia ou para todos os módulos</p></td></tr><tr><td><p><br></p></td><td><p><code>start-gui.sh</code>, <code>stop-gui.sh</code></p></td><td><p>Inicia ou para apenas módulos GUI</p></td></tr><tr><td><p><strong>Backup e Restauração</strong></p></td><td><p><code>export-backup.sh</code>, <code>import-backup.sh</code></p></td><td><p>Exporta e restaura configurações e backups do MongoDB</p></td></tr><tr><td><p><strong>Diagnósticos</strong></p></td><td><p><code>troubleshooting.sh</code>, <code>get_logs.sh</code></p></td><td><p>Verificações de sistema e coleta de logs</p></td></tr><tr><td><p><strong>Manutenção de Disco</strong></p></td><td><p><code>docker-images-housekeeping.sh</code></p></td><td><p>Limpa imagens Docker não utilizadas</p></td></tr><tr><td><p><br></p></td><td><p><code>housekeeping_viewtinet_logger_folder.sh</code></p></td><td><p>Limpa pastas locais de log</p></td></tr><tr><td><p><strong>Informações do Sistema</strong></p></td><td><p><code>get_node_ip.sh</code>, <code>check_ip.sh</code>, <code>check_vrrp.sh</code></p></td><td><p>Recupera informações de IP/VRRP</p></td></tr><tr><td><p><strong>Utilitários</strong></p></td><td><p><code>init.sh</code>, <code>exec_job.sh</code>, <code>uncompress-file.sh</code>, <code>update-repo.sh</code></p></td><td><p>Várias ferramentas de apoio</p></td></tr></tbody></table>

---

## **Scripts de Backup e Restauração: Uso Detalhado**

A Viewtinet inclui dois scripts principais para gerenciar as operações de backup e restauração:

-   `export-backup.sh`: Cria um backup da configuração essencial e dos componentes de dados.
-   `import-backup.sh`: Restaura um backup gerado anteriormente.

Estes scripts são projetados para ajudar os administradores a preservar e recuperar rapidamente o estado do sistema, especialmente durante migrações, atualizações ou recuperação de incidentes.

<br />

## **Criando um Backup (**`export-backup.sh`**)**

**Localização:**<br />
`/opt/vn/viewtinet-builder/scripts/export-backup.sh`

**Uso:**

```bash
/opt/vn/viewtinet-builder/scripts/export-backup.sh /path/to/backup-dir/
```

Este script executa as seguintes ações:

1.  Valida que um caminho de diretório de backup foi fornecido.
2.  Cria uma pasta com data e hora no local especificado.
3.  Arquiva o conteúdo de:
    
    -   `/opt/vn/viewtinet-builder` → scripts e binários da plataforma
    -   `/opt/vn/config` → configuração completa do sistema e dos módulos
4.  Usa `docker exec` e `mongodump` para extrair o conteúdo do banco de dados MongoDB rodando dentro do contêiner `viewtiauth`.
5.  Comprime todas as pastas geradas (`viewtinet-builder`, `config`, e o dump do MongoDB) em arquivos de arquivo `.tgz`.

**Exemplo de Saída no Diretório de Backup:**

```
config_viewtinet_bk_1681234567.tgz
viewtinet_builder_viewtinet_bk_1681234567.tgz
viewtiauth_viewtinet_bk_1681234567.tgz
```

---

## **Restaurando um Backup (**`import-backup.sh`**)**

**Localização:**<br />
`/opt/vn/viewtinet-builder/scripts/import-backup.sh`

**Uso:**

```bash
/opt/vn/viewtinet-builder/scripts/import-backup.sh /path/to/backup-dir/
```

Este script restaura apenas o **banco de dados MongoDB** usado pelo módulo `viewtiauth`. Ele executa as seguintes etapas:

1.  Valida a existência do arquivo `.tgz` do MongoDB no diretório especificado.
2.  Extrai o arquivo e copia o dump do MongoDB para o contêiner `viewtiauth_viewtinet-viewtiauth-mongo_1` usando `docker cp`.
3.  Executa `mongorestore` dentro do contêiner para reimportar os dados.
4.  Limpa arquivos temporários após a conclusão.

> ⚠️ **Atenção:** Este processo **sobrescreve** o banco de dados atual do `viewtiauth`. Ele deve ser realizado apenas quando o módulo estiver parado e durante operações de recuperação controladas.

---

#### 🧠 Notas e Recomendações

-   Estes scripts devem ser executados como o usuário `viewtinet` — nenhum `sudo` é necessário.
-   Sempre garanta que a plataforma ou o módulo afetado (ex., `viewtiauth`) esteja parado antes de realizar uma restauração.
-   Para obter um retrato completo da plataforma, combine isso com uma operação `stop-all.sh`.
-   Armazene as pastas de backup de forma segura e verifique a integridade antes de restaurar.
-   Use práticas consistentes de nomenclatura e arquivamento para os diretórios de backup.

> 💡 Inclua uma cópia dos arquivos `.tgz` gerados ao entrar em contato com o suporte para assistência de recuperação.

---

## **Tabela Resumo dos Scripts de Backup**

<table><tbody><tr><th><p>Script</p></th><th><p>Descrição</p></th><th><p>Inclui</p></th></tr><tr><td><p><code>export-backup.sh</code></p></td><td><p>Cria um backup de configurações e do MongoDB para o <code>viewtiauth</code></p></td><td><p><code>/opt/vn/viewtinet-builder</code>, <code>/opt/vn/config</code>, <code>mongodump</code></p></td></tr><tr><td><p><code>import-backup.sh</code></p></td><td><p>Restaura os dados do MongoDB do <code>viewtiauth</code> a partir do backup</p></td><td><p>Extrai, copia e restaura com o <code>mongorestore</code></p></td></tr></tbody></table>

> ✅ Recomendado: execute o `export-backup.sh` regularmente e antes de qualquer atualização ou grande alteração.

<br />