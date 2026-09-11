---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Chave-Valor (Key-Value)'
id: ZIX-2MR-SWE-6VG
slug: key-value
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 12:00:00'
---
# **<span align="center">Key Value</span>**

<br />

O handler de grid **Key Value** é projetado para analisar e extrair valores de uma string ou registro que contém dados em um formato delimitado de chave-valor (por exemplo, `key1=value1,key2=value2,key3=value3,key_n=value-n`). 

Ao usar este handler, o sistema cria automaticamente novas colunas no banco de dados correspondentes às chaves encontradas no registro, e as preenche com seus valores associados.

---

## **Contexto e Caso de Uso**

Um caso de uso muito comum para este handler de grid envolve integrações com dispositivos de rede e appliances de segurança (como firewalls ou sistemas de detecção de intrusão) que exportam logs de eventos via Syslog. Esses logs usam frequentemente o **CEF (Common Event Format)**, que encapsula vários campos de dados dentro de uma única carga útil de mensagem como pares de chave-valor. 

Para obter mais informações sobre o formato CEF, você pode consultar a documentação oficial [Micro Focus ArcSight CEF documentation](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors-8.3/cef-implementation-standard/) ou padrões da indústria semelhantes.

O uso do handler de grid **Key Value** em uma coluna `syslog_record` permite que o processo ETL exploda a carga CEF e indexe adequadamente cada propriedade em sua própria coluna.

<br />

---

## **Etapas de Configuração**

A configuração do handler de grid **Key Value** envolve as seguintes etapas sequenciais:

1. **Adicionar o Grid-Handler**: Clique no botão "ADD NEW GRID-HANDLER" e selecione **Key Value** no menu suspenso `Grid Handler Type`.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/key-value-overview.png" align="center"></figure>

<br />

2. **Selecionar a Message Column**: No menu suspenso `Message Column`, selecione o campo que contém a string bruta de chave-valor. Normalmente, para eventos Syslog, esta coluna é `syslog_record`.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/key-value-step3.png" align="center"></figure>

<br />

3. **Definir Output Fields**: Clique no ícone de lápis (<i class="fa fa-pencil"></i>) para editar os campos de saída (Output Fields). Isso abrirá um pop-up de editor de texto onde você pode definir quais chaves serão extraídas para novas colunas.
   
   > [!TIP]
   > A maneira mais fácil de configurar isso é preparar a lista de campos separados por vírgulas em um editor de texto simples, colar a string inteira na caixa de entrada, pressionar Enter e, em seguida, clicar em **SAVE**.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/key-value-step4.png" align="center"></figure>

<br />

4. **Habilitar o Cabeçalho CEF (Opcional)**: Se os logs de entrada seguirem o Common Event Format (CEF), certifique-se de marcar a caixa de seleção **"Has CEF Header"**. Isso instrui o analisador a lidar com o prefixo padrão CEF antes de extrair os pares chave-valor.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/key-value-step5.png" align="center"></figure>

<br />