---
reusableId: 180
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtisight integration'
id: DQQ-811-GFO-MAV
slug: viewtisight-integration
isVisible: true
isSearchable: true
lastUpdated: '2026-06-02 08:55:09'
---
# **<span align="center">VIEWTISIGHT INTEGRATION</span>**

<br />

Viewtisight integration is done via iframes mainly. In this section, steps to integrate Viewtisight into 3rd party GUIs are exposed.

<br />

## **Authentication token**

Tokens can be obtained as explained in the Authentication section or a similar POST request done via the browser.

Note that if no token is requested, the iframe will redirect to the Viewtiauth interface to generate a new one graphically.

<br />

## **Embedding Dashboards**

Dashboards created from Viewtisight can be embedded into 3rd party GUIs. The URL format to be used in iframes is as follows:

`$VIEWTISIGHT_URL/dashboard/$dashboard_name?hidePanels=true&auth=$TOKEN`

Where `$TOKEN` is the cipher value obtained as explained in the Authentication section (not to be confused with `access_token`, which is used for API calls).

For example, given the following dashboard:

`http://192.168.1.187:8080/dashboard/viewtimon`

The iframe URL is:

```html
<iframe src="http://192.168.1.187:8080/dashboard/viewtimon?hidePanels=true&auth=53616c7465645f5fd17d746a9c20566c6859d8ca0ab12abede705faf3214160d00200647517d8e2f7318bb5bc8c8269d1d66fbb60e30de5c206a861becfed79c9392410fa8065823b4316a36459c8e12a4d04896675e116cd3289d322baa5e30e9308d2ede2ff804ec34fd879250e47d840f93c4c80f3d398f90fa52f503326d1285cc9f8c622c52679ff944ba9f3fdbeb582c7c22ad496ac351ce5bb0e31255a04532981536f728e314389b8dd49a60e8ef8cca119d3fc13ac2547f3d4dd1a48dcc3abe822481c96b68ab1db25b79139d73531647befb9760ee67e44e1e3410c21d7c3c9684a167ca1aaf8cd1dcfd5c" width="100%"></iframe>
```

<br />

### **URL Parameters**

-   `hidePanels`: Indicates whether panels should be hidden or not. Possible values: `true`/`false` (`true` recommended for iframes).
-   `auth`: Authentication Token to be able to perform queries. _Note: If no token is set in the prior url, the iframe window will redirect to the Viewtiauth interface to generate a new one graphically._

<br />

## **Embedding Cards**

Cards created from dashboards can be isolated via URL to only visualize a specific card given its id.

The URL to embed a specific card from any dashboard is as follows:

`$VIEWTISIGHT_URL/dashboard/$dashboard_name?cardId=$CARD_ID&auth=$TOKEN`

<br />

### **URL Parameters**

-   `cardId`: Card ID to filter in the dashboard. These steps can be performed in order to get the `card_id`:
    
    1.  Click on the button on top right of the card and click on **Edit**:<br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img8.png" align="center"></figure>
        
        <br />
        
    2.  The Card builder will appear. Click on the **Raw Data** section and copy the content from the `card_id` attribute:<br />
        
        <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/api-integration-img9.png" align="center"></figure>
        
        <br />
        
-   `auth`: Authentication Token to be able to perform queries. _Note: If no token is set in the prior url, the iframe window will redirect to the Viewtiauth interface to generate a new one graphically._

<br />