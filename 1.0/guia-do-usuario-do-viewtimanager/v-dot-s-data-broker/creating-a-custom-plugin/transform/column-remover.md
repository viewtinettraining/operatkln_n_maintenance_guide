---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Removedor de Coluna'
id: RVF-1N2E-SDZ-KI3
slug: column-remover
isVisible: true
isSearchable: true
lastUpdated: '2026-05-20 15:20:00'
---
# **<span align="center">Column Remover</span>**

<br />

O handler de grid **Column Remover** é um componente de transformação que permite remover arbitrariamente qualquer campo (coluna) da **Grid** durante o pipeline ETL (Extração, Transformação, Carga).

Esta operação é particularmente útil em dois cenários principais:
- **Otimização de Banco de Dados & Segurança**: Evitar que campos sensíveis, redundantes ou desnecessários sejam gravados no banco de dados, economizando espaço de armazenamento e aderindo às políticas de privacidade de dados.
- **Limpeza de Dados Intermediários**: Remover colunas temporárias que foram criadas apenas para cálculos intermediários por outros handlers de grid upstream (como `math-operation` ou scripts personalizados), garantindo que o conjunto de dados final carregado permaneça limpo e conciso.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/column-remover.png" align="center"></figure>

<br />

---

### **Configuração**

A configuração do **Column Remover** requer a especificação de apenas um campo:

- **Column**: Um menu suspenso contendo todas as colunas disponíveis na estrutura atual da Grid. Selecione a coluna específica que deseja descartar (por exemplo, `memory_used` como mostrado na captura de tela acima).

Uma vez que este handler é executado, a coluna selecionada é completamente eliminada da Grid ativa e não estará disponível em etapas subsequentes de transformação ou na fase de carga final.

<br />

---

### **Ordem de Execução & Validação**

Devido à natureza destrutiva de remover uma coluna do pipeline, o **Column Remover** tem uma restrição rigorosa de ordenação:

- **Requisito de Posicionamento**: O Column Remover **deve** ser posicionado no final da lista de todos os handlers de grid configurados na etapa de ETL.
- **Regra de Validação**: Se um Column Remover for colocado antes de qualquer outro handler de grid na sequência, o sistema impedirá o salvamento da configuração e exibirá uma mensagem de erro de validação vermelha sob o campo de seleção do handler:  
  `This grid must be at the end of this stage` (como ilustrado abaixo).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/column-remover-error.png" align="center"></figure>

<br />

<div class="sd-callout" data-callout-type="warning"><strong>Aviso:</strong> Certifique-se sempre de que todas as outras etapas de transformação (como <em>math-operation</em>, filtros ou handlers de formatação) que dependem de uma coluna específica sejam executadas <strong>antes</strong> do Column Remover eliminá-la.</div>

<br />

<div class="sd-callout" data-callout-type="tip"><strong>Melhor Prática:</strong> É altamente recomendável usar o Column Remover para limpar quaisquer variáveis temporárias ou intermediários matemáticos imediatamente após terem cumprido seu propósito em handlers downstream, como <em>math-operation</em>. Isso mantém o esquema de dados limpo e otimizado.</div>

<br />
