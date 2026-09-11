---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Tenants'
id: 70B-79M2-SF8-1QC
slug: tenants
isVisible: true
lastUpdated: '2025-10-15 15:29:46'
---
# **<span align="center">Inquilinos (Tenants)</span>**

<span align="justify">Cada inquilino (tenant) tem acesso a um portal dedicado com insights em tempo real apenas dos dados e painéis (dashboards) que você conceder a ele. Você pode criar portais para clientes individuais para agregar valor e reduzir o cancelamento de clientes (churn) — ou criar inquilinos internos para diferentes equipes dentro de sua organização.</span>

As seções a seguir descrevem como configurar inquilinos na visualização **Admin → Tenants**.

## **Criar ou Editar um Inquilino**

1.  Navegue até **Admin → Tenants**.
2.  Clique em **Add Tenant** (ou selecione um inquilino existente e clique em **Edit**).

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/HIHzXeA0eG2pbKEscM0o.png" alt="Tenants List"></figure>

## **Detalhes do Inquilino**

Defina os metadados básicos para seu inquilino:

<table><tbody><tr><th><p>Campo</p></th><th><p>Descrição</p></th></tr><tr><td><p><strong>Nome (Name)</strong></p></td><td><p>Um identificador curto e exclusivo para o portal do inquilino.</p></td></tr><tr><td><p><strong>Descrição (Description)</strong></p></td><td><p>Texto livre opcional para descrever o caso de uso ou o proprietário do inquilino.</p></td></tr><tr><td><p><strong>Criado Em (Created At)</strong></p></td><td><p>Carimbo de data/hora de leitura (read-only) de quando o inquilino foi criado.</p></td></tr><tr><td><p><strong>Última Atualização (Last Updated)</strong></p></td><td><p>Carimbo de data/hora de leitura (read-only) da alteração mais recente.</p></td></tr></tbody></table>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/pIzzq6INndPRg146y6jW.png" alt="Tenant Details" align="center"></figure>

<br />

## **Configuração de Conjuntos (Sets Config)**

Controle quais fontes de dados cada inquilino pode ver, e em qual nível de acesso:

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/EOyfjyu3GxPhoRcWTrVb.png" alt="Tenant Sets Config" align="center"></figure>

<br />

<table><tbody><tr><th><p>Coluna</p></th><th><p>Significado</p></th></tr><tr><td><p><strong>↕ Mover (Move)</strong></p></td><td><p>Arraste ou clique para reordenar como os conjuntos de dados aparecem no portal do inquilino.</p></td></tr><tr><td><p><strong>Conjunto (Set)</strong></p></td><td><p>Nome da fonte de dados ou painel (ex: “DPI Records”, “NetFlow Metrics”).</p></td></tr><tr><td><p><strong>Acesso (Access)</strong></p></td><td><p>Selecione um dos seguintes:<br>- <strong>Full (Total)</strong>: o inquilino pode visualizar, consultar e exportar.<br>- <strong>Partial (Parcial)</strong>: o inquilino vê apenas um subconjunto filtrado (requer <strong>Field</strong>, <strong>Type</strong> e <strong>Values</strong>).<br>- <strong>None (Nenhum)</strong>: oculto.</p></td></tr><tr><td><p><strong>Campo (Field)</strong></p></td><td><p><em>(Somente se Parcial)</em> O campo do esquema usado para particionar os dados (ex: <code>customer_id</code>, <code>region</code>).</p></td></tr><tr><td><p><strong>Tipo (Type)</strong></p></td><td><p><em>(Somente se Parcial)</em> Escolha um:<br>- <code>IP</code> (endereço único)<br>- <code>IP Range</code> (Faixa de IP, ex: <code>10.0.0.1-10.0.0.255</code>)<br>- <code>Subnet</code> (Sub-rede, ex: <code>192.168.1.0/24</code>)<br>- <code>Identifier</code> (campo de banco de dados decorado).</p></td></tr><tr><td><p><strong>Valores (Values)</strong></p></td><td><p><em>(Somente se Parcial)</em> Lista de valores permitidos separados por vírgula, correspondendo ao <strong>Tipo (Type)</strong>.</p></td></tr></tbody></table>

> **Nota:** Ao escolher **Identifier** como o tipo de campo, você está se referindo a uma coluna "decorada" no banco de dados — uma que foi gerada ou enriquecida pelo Visual Smart Data Broker. Para saber mais sobre como esses campos decoradores funcionam (e como configurá-los), veja o capítulo **V.S. Data Broker**.
> 
> **Dica Pro:** Marcar a caixa de seleção **Access** na linha superior aplica essa permissão a _todos_ os conjuntos de dados. Não se esqueça de clicar em **Save Changes** na parte inferior da página!

## <br />
**Usuários do Inquilino (Tenant Users)**

Esta seção lista quais usuários pertencem a este inquilino.<br />
Para adicionar ou remover usuários, acesse **Admin → Users**, selecione um usuário e atribua-o ao inquilino desejado.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/okym54ss97OzUoFtryn4.png" alt="Tenant Users"></figure>

<div class="sd-callout" data-callout-type="tip">Dica: Sempre clique em <strong>Save Changes</strong> após modificar qualquer configuração de inquilino.</div>

<br />