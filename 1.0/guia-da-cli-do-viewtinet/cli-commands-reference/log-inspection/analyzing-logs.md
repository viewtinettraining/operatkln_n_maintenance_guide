---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Analisando Logs'
id: ABY-3TLV-XA4-MNN
slug: analyzing-logs
isVisible: true
lastUpdated: '2025-10-15 16:06:47'
---
# **<span align="center">Analisando Logs no Viewtinet</span>**

A análise de logs é uma parte fundamental da operação e solução de problemas da plataforma Viewtinet. Existem duas maneiras principais de acessar os logs em um ambiente Viewtinet:

1.  **Acessando arquivos históricos de log armazenados no disco**
2.  **Inspecionando os logs diretamente dos contêineres em execução usando** `docker logs`

Cada método serve a casos de uso diferentes e possui suas vantagens e desvantagens. Este capítulo descreve ambas as abordagens em detalhes e mostra como usá-las de forma eficaz.

---

## **Método 1:**

### Visualizando Logs de `/var/log/viewtinet`

<br />

Os módulos do Viewtinet gravam seus logs em arquivos no diretório:

```
/var/log/viewtinet/
```

Cada módulo possui seu próprio arquivo de log. Alguns exemplos dos arquivos que você pode encontrar incluem:

```
viewtinet-active-probe.log
viewtinet-haproxy.log
viewtinet-timescaledb.log
viewtinet-viewtimanager.log
viewtinet-bypasser.log
viewtinet-kafka.log
viewtinet-viewtiauth.log
viewtinet-viewtimon.log
viewtinet-dhyana.log
viewtinet-license-cheker.log
viewtinet-viewticore.log
viewtinet-viewtisight.log
```

Esses arquivos armazenam logs **historicamente e de forma persistente**, mesmo após o reinício dos contêineres ou do sistema.

<br />

#### 🔍 Exemplo de comando:

```bash
less /var/log/viewtinet/viewtinet-viewticore.log
```

Você também pode usar ferramentas como `grep` para filtrar mensagens:

```bash
grep ERROR /var/log/viewtinet/viewtinet-viewtimanager.log
```

#### ✅ Vantagens:

-   Os dados históricos a longo prazo estão disponíveis.
-   Os logs de todos os contêineres de um módulo são consolidados.
-   Mais fácil para análises forenses ou investigações de causa raiz.

#### ⚠️ Desvantagens:

-   Os logs podem ser extensos e difíceis de pesquisar sem filtros.
-   Não é ideal para verificações rápidas específicas de um contêiner.

---

## **Método 2:**

### Usando `docker logs &lt;container&gt;`

<br />

Você também pode inspecionar os logs diretamente de um contêiner em execução específico usando o comando `docker logs`. Isso fornece os logs **em tempo real** ou os mais recentes de um contêiner específico.

<br />

#### 🔍 Exemplo de comando:

```bash
docker logs viewtimanager_viewtinet-viewtimanager-backend_1
```

Para seguir os logs ao vivo:

```bash
docker logs -f viewtiauth_viewtinet-viewtiauth-backend_1
```

Este método é ideal para monitorar o comportamento imediato após reiniciar um serviço ou ao depurar um contêiner que não está funcionando adequadamente.

<br />

#### ✅ Vantagens:

-   Os logs são exibidos em tempo real.
-   Focado em um único contêiner — mais preciso.
-   Útil para depuração ativa.

#### ⚠️ Desvantagens:

-   Em ambientes de alto tráfego, os logs podem incluir apenas os **últimos minutos**.
-   Não é persistente — os logs são perdidos se o contêiner for removido.

---

## **Escolhendo o Método Correto**

<br />

<table><tbody><tr><th><p>Caso de Uso</p></th><th><p>Método Recomendado</p></th></tr><tr><td><p>Análise histórica</p></td><td><p><code>/var/log/viewtinet</code></p></td></tr><tr><td><p>Depuração em tempo real</p></td><td><p><code>docker logs</code></p></td></tr><tr><td><p>Filtrando erros em todos os logs</p></td><td><p><code>/var/log/viewtinet + grep</code></p></td></tr><tr><td><p>Problemas específicos de contêineres</p></td><td><p><code>docker logs &lt;container&gt;</code></p></td></tr><tr><td><p>Verificação após o reinício</p></td><td><p><code>docker logs -f</code></p></td></tr></tbody></table>

> **Dica:** Você pode combinar ambos os métodos para uma visualização completa — comece com `docker logs` para a atividade recente, e utilize os logs baseados em arquivos para obter um contexto mais profundo.

<br />