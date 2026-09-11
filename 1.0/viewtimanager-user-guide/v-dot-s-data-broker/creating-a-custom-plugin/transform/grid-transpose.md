---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grid Transpose'
id: 9XM-YVZ-OY1-MTB
slug: grid-transpose
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 11:10:35'
---
# **<span align="center">Grid Transpose</span>**

<br />

O handler **Grid Transpose** remodela fundamentalmente a estrutura da sua grid de dados. Ele converte uma linha larga contendo várias colunas individuais em um formato longo de "chave-valor" (frequentemente chamado de modelo Entidade-Atributo-Valor), criando várias linhas a partir de uma única linha original.

## **Quando usá-lo?**

Este handler é extremamente útil ao integrar com bancos de dados de séries temporais ou sistemas de monitoramento que esperam dados em um esquema estrito de `metric_name` e `metric_value` em vez de tabelas largas. Ao transpor a grid, você normaliza dados altamente dimensionais em uma estrutura chave-valor padrão e escalável.

---

## **Parâmetros de Configuração**

Para configurar o handler, você precisa definir qual(is) coluna(s) atuará(ão) como ponto de ancoragem para a transposição:

-   **Grid Handler Type**: Selecione `Grid Transpose`.
-   **Keys**: Selecione a coluna que deve ser mantida como a chave primária constante em todas as novas linhas transpostas geradas. Geralmente, a coluna `timestamp` é selecionada aqui para garantir que todas as novas linhas de métrica geradas mantenham a chave temporal exata do evento original.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-transpose-step1.png" align="center"></figure>

<br />

---

## **Comportamento Esperado**

O exemplo a seguir demonstra como uma linha larga da grid é transposta para uma estrutura longa.

**Grid Original (Formato largo):**

<table><tbody><tr><th><p>timestamp</p></th><th><p>host</p></th><th><p>name</p></th><th><p>network</p></th><th><p>rtt_min</p></th><th><p>rtt_avg</p></th><th><p>rtt_max</p></th><th><p>rtt_mdev</p></th><th><p>packet_loss</p></th><th><p>reply</p></th><th><p>status</p></th><th><p>hostname</p></th><th><p>operating_system</p></th><th><p>role</p></th><th><p>snmp</p></th><th><p>type</p></th><th><p>vendor</p></th><th><p>version</p></th></tr><tr><td><p><code>1779447362814887</code></p></td><td><p><code>10.30.23.151</code></p></td><td><p><br></p></td><td><p><br></p></td><td><p><code>430</code></p></td><td><p><code>584</code></p></td><td><p><code>1110</code></p></td><td><p><code>263</code></p></td><td><p><code>0</code></p></td><td><p><code>1</code></p></td><td><p><code>alive</code></p></td><td><p><code>rds151.viewtinet.local</code></p></td><td><p><code>Windows</code></p></td><td><p><code>Remote Desktop for Student</code></p></td><td><p><code>NO</code></p></td><td><p><code>Virtual Machine</code></p></td><td><p><code>Microsoft</code></p></td><td><p><code>10</code></p></td></tr></tbody></table>

<br />

Quando o handler **Grid Transpose** é aplicado com o campo `Keys` definido como `timestamp`, a grid gera uma estrutura completamente nova com os nomes de colunas padrão `field`, `value` e `field_value`:

**Grid Transposta (Formato longo):**

<table><tbody><tr><th><p>timestamp</p></th><th><p>field</p></th><th><p>value</p></th><th><p>field_value</p></th></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>host</code></p></td><td><p><code>10.30.23.151</code></p></td><td><p><code>host=10.30.23.151</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>name</code></p></td><td><p><br></p></td><td><p><code>name=</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>network</code></p></td><td><p><br></p></td><td><p><code>network=</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>rtt_min</code></p></td><td><p><code>380</code></p></td><td><p><code>rtt_min=380</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>rtt_avg</code></p></td><td><p><code>1440</code></p></td><td><p><code>rtt_avg=1440</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>rtt_max</code></p></td><td><p><code>5090</code></p></td><td><p><code>rtt_max=5090</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>rtt_mdev</code></p></td><td><p><code>1826</code></p></td><td><p><code>rtt_mdev=1826</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>packet_loss</code></p></td><td><p><code>0</code></p></td><td><p><code>packet_loss=0</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>reply</code></p></td><td><p><code>1</code></p></td><td><p><code>reply=1</code></p></td></tr><tr><td><p><code>1779447422672874</code></p></td><td><p><code>status</code></p></td><td><p><code>alive</code></p></td><td><p><code>status=alive</code></p></td></tr></tbody></table>

> _Nota: Por uma questão de brevidade, apenas os primeiros 10 campos são mostrados, mas o handler itera por todas as colunas originais._

<br />

### **Explicação:**

-   A chave configurada (`timestamp`) é preservada como âncora em cada nova linha.
-   O nome original da coluna torna-se o `field`.
-   Os dados originais dentro dessa coluna tornam-se o `value`.
-   O handler cria automaticamente uma coluna `field_value` concatenando ambos usando um sinal `=`.

<br />