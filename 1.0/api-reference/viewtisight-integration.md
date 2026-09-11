---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Integração com o Viewtisight'
id: DQQ-811-GFO-MAV
slug: viewtisight-integration
isVisible: true
isSearchable: true
lastUpdated: '2026-06-02 08:55:09'
---
# **<span align="center">INTEGRAÇÃO DO VIEWTISIGHT</span>**

<br />

A integração do Viewtisight é feita principalmente via iframes. Nesta seção, são expostos os passos para integrar o Viewtisight em interfaces gráficas (GUIs) de terceiros.

<br />

## **Token de Autenticação**

Os tokens podem ser obtidos conforme explicado na seção de Autenticação ou por meio de uma requisição POST semelhante feita via navegador.

Note que se nenhum token for solicitado, o iframe redirecionará para a interface do Viewtiauth para gerar um novo graficamente.

<br />

## **Incorporando Dashboards**

Dashboards criados no Viewtisight podem ser incorporados em interfaces gráficas (GUIs) de terceiros. O formato da URL a ser usado em iframes é o seguinte:

`$VIEWTISIGHT_URL/dashboard/$dashboard_name?hidePanels=true&auth=$TOKEN`

Onde `$TOKEN` é o valor da cifra obtido conforme explicado na seção de Autenticação (não deve ser confundido com `access_token`, que é usado para chamadas de API).

Por exemplo, dado o seguinte dashboard:

`http://192.168.1.187:8080/dashboard/viewtimon`

A URL do iframe é:

```html
<iframe src="http://192.168.1.187:8080/dashboard/viewtimon?hidePanels=true&auth=53616c7465645f5fd17d746a9c20566c6859d8ca0ab12abede705faf3214160d00200647517d8e2f7318bb5bc8c8269d1d66fbb60e30de5c206a861becfed79c9392410fa8065823b4316a36459c8e12a4d04896675e116cd3289d322baa5e30e9308d2ede2ff804ec34fd879250e47d840f93c4c80f3d398f90fa52f503326d1285cc9f8c622c52679ff944ba9f3fdbeb582c7c22ad496ac351ce5bb0e31255a04532981536f728e314389b8dd49a60e8ef8cca119d3fc13ac2547f3d4dd1a48dcc3abe822481c96b68ab1db25b79139d73531647befb9760ee67e44e1e3410c21d7c3c9684a167ca1aaf8cd1dcfd5c" width="100%"></iframe>
```

<br />

### **Parâmetros da URL**

-   `hidePanels`: Indica se os painéis devem ser ocultados ou não. Valores possíveis: `true`/`false` (`true` é recomendado para iframes).
-   `auth`: Token de Autenticação para poder executar consultas. _Nota: Se nenhum token for definido na url anterior, a janela do iframe redirecionará para a interface do Viewtiauth para gerar um novo graficamente._

<br />

## **Incorporando Cartões (Cards)**

Cartões criados a partir de dashboards podem ser isolados via URL para visualizar apenas um cartão específico através de seu id.

A URL para incorporar um cartão específico de qualquer dashboard é a seguinte:

`$VIEWTISIGHT_URL/dashboard/$dashboard_name?cardId=$CARD_ID&auth=$TOKEN`

<br />

### **Parâmetros da URL**

-   `cardId`: ID do cartão a ser filtrado no dashboard. Os seguintes passos podem ser realizados para obter o `card_id`:
    
    1.  Clique no botão no canto superior direito do cartão e clique em **Edit** (Editar):<br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img8.png" align="center"></figure>
        
        <br />
        
    2.  O construtor de cartão aparecerá. Clique na seção **Raw Data** (Dados Brutos) e copie o conteúdo do atributo `card_id`:<br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img9.png" align="center"></figure>
        
        <br />
        
-   `auth`: Token de Autenticação para poder executar consultas. _Nota: Se nenhum token for definido na url anterior, a janela do iframe redirecionará para a interface do Viewtiauth para gerar um novo graficamente._

<br />