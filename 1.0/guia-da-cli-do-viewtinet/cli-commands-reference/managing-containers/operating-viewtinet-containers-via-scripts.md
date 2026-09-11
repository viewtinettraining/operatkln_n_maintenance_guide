---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Operando Contêineres Viewtinet via Scripts'
id: 20U-C19U-8N7-KWB
slug: operating-viewtinet-containers-via-scripts
isVisible: true
lastUpdated: '2025-10-15 16:05:16'
---
# **<span align="center">Operando Contêineres Viewtinet via Scripts</span>**

<br />

Este capítulo aborda o uso de scripts CLI para gerenciar o ciclo de vida dos contêineres Viewtinet. Estes scripts fornecem uma maneira segura e consistente de iniciar, parar ou reiniciar todos os contêineres que pertencem a um módulo específico do Viewtinet.

Os scripts estão localizados no seguinte caminho:

```
/opt/vn/viewtinet-builder/scripts/<module>/action-module.sh
```

Onde `&lt;module&gt;` corresponde a um dos componentes da plataforma, tais como:

-   `viewtiauth`
-   `viewtisight`
-   `viewtimanager`
-   `viewticore`
-   `dhyana`
-   `viewtimon`

Cada script aceita um dos seguintes parâmetros:

-   `start`: Inicia todos os contêineres do módulo selecionado.
-   `stop`: Para todos os contêineres do módulo selecionado.
-   `restart`: Para e depois inicia todos os contêineres do módulo selecionado.

Esses scripts garantem que as ações sejam aplicadas em todo o módulo de forma controlada, respeitando as dependências dos contêineres e a ordem necessária de inicialização/parada. Eles são especialmente úteis durante:

-   Operações de manutenção ou solução de problemas
-   Desligamentos controlados antes de atualizações do sistema
-   Reinícios parciais quando apenas um módulo exige atenção

---

<br />

## **Iniciando um Módulo**

Para iniciar todos os contêineres associados a um módulo específico do Viewtinet, use o parâmetro `start` com o script `action-module.sh` do módulo.

**Exemplo:**

```bash
/opt/vn/viewtinet-builder/scripts/viewticore/action-module.sh start
```

> **Dica:** Aguarde alguns segundos após executar o script, em seguida verifique o status do contêiner usando `dps`.

## **Parando um Módulo**

Para parar todos os contêineres associados a um módulo específico, use o parâmetro `stop`. Isso é útil antes de aplicar atualizações, fazer backup de volumes ou realizar diagnósticos.

**Exemplo:**

```bash
/opt/vn/viewtinet-builder/scripts/viewtisight/action-module.sh stop
```

> **Atenção:** Não use isso durante os horários de pico de produção, a menos que seja necessário.

<br />

## **Reiniciando um Módulo**

O parâmetro `restart` combina uma operação de parada seguida de uma inicialização para o módulo selecionado. Isso é comumente usado para recuperar de problemas a nível de contêiner, alterações de configuração ou vazamentos de memória.

<br />

**Exemplo:**

```bash
/opt/vn/viewtinet-builder/scripts/viewtiauth/action-module.sh restart
```

> **Nota:** Um reinício pode interromper temporariamente os serviços. Sempre verifique a saúde da plataforma depois usando `dps` e a interface web.

---

## **Scripts Adicionais para o Módulo** `viewticore`

Ao contrário de outros módulos no Viewtinet, o módulo `viewticore` inclui dois scripts adicionais para gerenciar componentes internos separadamente:

1.  `action-timescaledb.sh`
2.  `action-viewticore-internal.sh`

Estes scripts fornecem controle mais granular sobre componentes de infraestrutura críticos relacionados ao armazenamento de dados e lógica interna da plataforma.

<br />

## **Reiniciando o Banco de Dados de Séries Temporais (**`action-timescaledb.sh`**)**

Este script controla o contêiner do TimescaleDB, que atua como o banco de dados de séries temporais onde todos os dados coletados são armazenados.

**Caminho do script:**

```
/opt/vn/viewtinet-builder/scripts/viewticore/action-timescaledb.sh
```

**Uso:**

```bash
/opt/vn/viewtinet-builder/scripts/viewticore/action-timescaledb.sh restart
```

Este script também aceita os parâmetros `start` e `stop`:

```bash
/opt/vn/viewtinet-builder/scripts/viewticore/action-timescaledb.sh stop
/opt/vn/viewtinet-builder/scripts/viewticore/action-timescaledb.sh start
```

> **Nota:** Parar o banco de dados interromperá o acesso a todas as métricas e dados históricos. Use com cautela e apenas durante janelas de manutenção planejadas.

<br />

## **Gerenciando Contêineres Internos (**`action-viewticore-internal.sh`**)**

Este script lida com contêineres auxiliares que realizam o processamento em segundo plano dentro do módulo `viewticore`, como processos de árbitro ou o MongoDB usado para coordenação interna.

<br />

**Caminho do script:**

```
/opt/vn/viewtinet-builder/scripts/viewticore/action-viewticore-internal.sh
```

**Uso:**

```bash
/opt/vn/viewtinet-builder/scripts/viewticore/action-viewticore-internal.sh restart
```

> **Dica:** Use este script ao solucionar alarmes internos, problemas de replicação ou se for instruído pela equipe de suporte.

---

> ⚠️ **Aviso:** Estes scripts são destinados a cenários operacionais avançados. Evite usá-los a menos que você entenda seu impacto ou tenha sido instruído pelo suporte do Viewtinet. Na maioria dos casos, reiniciar o módulo `viewticore` completo usando `action-module.sh` é suficiente.

---

<br />

## **Tabela de Referência de Scripts de Módulos**

A tabela a seguir resume todos os módulos suportados e a localização do seu script de controle:

<table><tbody><tr><th><p><span align="center">Módulo</span></p></th><th><p><span align="center">Caminho do Script</span></p></th><th><p><span align="center">Descrição</span></p></th></tr><tr><td><p><code>viewtiauth</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewtiauth/action-module.sh</code></p></td><td><p>Contêineres de acesso de usuários e autenticação</p></td></tr><tr><td><p><code>viewtisight</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewtisight/action-module.sh</code></p></td><td><p>Painéis de BI e mecanismo de relatórios</p></td></tr><tr><td><p><code>viewtimanager</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewtimanager/action-module.sh</code></p></td><td><p>Interface web e orquestração de plugins</p></td></tr><tr><td><p><code>viewticore</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewticore/action-module.sh</code></p></td><td><p>Processamento principal e armazenamento de dados</p></td></tr><tr><td><p><code>viewticore-db</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewticore/action-timescaledb.sh</code></p></td><td><p>Controle do banco de dados de séries temporais (TimescaleDB)</p></td></tr><tr><td><p><code>viewticore-int</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewticore/action-viewticore-internal.sh</code></p></td><td><p>Serviços internos do módulo viewticore</p></td></tr><tr><td><p><code>dhyana</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/dhyana/action-module.sh</code></p></td><td><p>Pipelines de ETL e lógica de coleta de dados</p></td></tr><tr><td><p><code>viewtimon</code></p></td><td><p><code>/opt/vn/viewtinet-builder/scripts/viewtimon/action-module.sh</code></p></td><td><p>QoS e contêineres de visibilidade de rede</p></td></tr></tbody></table>

Use esta tabela como uma referência rápida para localizar e executar o script de controle correto para cada módulo no seu ambiente Viewtinet.