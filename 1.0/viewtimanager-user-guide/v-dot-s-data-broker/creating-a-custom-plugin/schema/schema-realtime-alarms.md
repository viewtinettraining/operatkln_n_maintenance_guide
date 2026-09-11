---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Real-Time Alarms'
id: WTM-6BK-1O0-RY2
slug: schema-realtime-alarms
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 18:48:00'
---
# **<span align="center">Alarmes em Tempo Real (Real-Time Alarms)</span>**

<br />

Além de definir a estrutura de dados, a **etapa de Schema** permite que os administradores configurem **Alarmes em Tempo Real**. A Viewtinet suporta tanto alarmes baseados em consulta (agendados) quanto alarmes em Tempo Real, mas esta etapa lida especificamente com os últimos.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarm-intro.png" align="center"></figure>

<br />

---

## **Entendendo a Avaliação em "Tempo Real"**

O termo "Tempo Real" neste contexto refere-se estritamente ao **momento exato em que os dados brutos estão sendo inseridos no banco de dados**. 

Durante o processo de ETL (Extrair, Transformar, Carregar), a métrica é capturada e simultaneamente encaminhada ao Módulo de Alarmes para avaliação imediata em relação a um limite (threshold). Esta abordagem **não** requer uma consulta programada (agendada) ao banco de dados.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarm-etl.png" align="center"></figure>

<br />

> [!WARNING] **Sincronismo de Avaliação e Frequência de Polling**
> Como a avaliação acontece no momento da inserção no banco de dados, a frequência real da avaliação do alarme depende inteiramente de sua frequência de polling de extração. Por exemplo, se você estiver usando um plugin SNMP que faz o polling de dados a cada **5 minutos**, a avaliação em "tempo real" ocorrerá a cada 5 minutos quando aquele lote de dados for inserido.

<br />

---

## **Configurando um Alarme em Tempo Real**

Para criar um novo alarme, role para baixo até a seção **Alarms** (Alarmes) dentro da configuração do Schema e siga estes passos:

**Passo 1:** Clique no botão **ADD ALARM** (Adicionar Alarme).

**Passo 2:** Forneça um nome descritivo para o **Alarm name** (Nome do Alarme).

**Passo 3:** No menu suspenso **Metrics** (Métricas), selecione a coluna métrica específica que você deseja monitorar (ex., `cpu_usage`, `interface-in-octets`).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarm-form.png" align="center"></figure>

<br />

---

### **Definindo Dimensões e Chaves do Alarme (Alarm Dimensions and Keys)**

**Passo 4:** Você deve adicionar as dimensões que acompanharão o alarme para fornecer contexto. Clique no botão **ADD NEW DIMENSION** (Adicionar Nova Dimensão).

**Passo 5:** Das dimensões adicionadas, você deve selecionar pelo menos uma dimensão para atuar como a **Chave (Key)**, marcando a sua caixa de seleção correspondente. 

> [!NOTE] **O que é uma Chave de Alarme (Alarm Key)?**
> Conforme indicado pela dica (tooltip) do sistema, se uma dimensão é marcada como uma **chave**, cada valor exclusivo dessa dimensão pode gerar um alarme distinto e separado. Por exemplo, se `host` for a chave, o sistema rastreia a métrica separadamente para cada endereço IP ou nome de host individual, gerando alarmes independentes para cada um que violar o limite (threshold).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarm-key.png" align="center"></figure>

<br />

---

### **Aplicando Filtros**

Por padrão, cada dimensão adicionada tem seu **Filtro (Filter)** definido como `Full` (Total). Isso significa que o alarme será avaliado em relação a todo o conjunto de dados que chega ao banco de dados para aquela métrica.

No entanto, você pode restringir o alarme para apenas avaliar segmentos específicos de sua rede:

**Passo 6:** Mude o menu suspenso Filter de `Full` para `Partial`.

**Passo 7:** Um menu suspenso **Filter Type** (Tipo de Filtro) aparecerá. Selecione os critérios de avaliação que deseja usar (ex., `IPs`, `IP range`, `Subnets`, `Identifiers`, `starts-with`, `contains`, `regex`).

**Passo 8:** No campo **Value** (Valor) à direita, insira a string específica, o IP ou o padrão regex em relação ao qual os dados devem ser avaliados.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarm-filter.png" align="center"></figure>

<br />

Uma vez definida a estrutura do alarme aqui na etapa de Schema, as regras reais (Severity / Gravidade, Condition Thresholds / Limites de Condição e Actions / Ações como Email ou Telegram) são configuradas posteriormente a partir da interface do **Viewtisight**.