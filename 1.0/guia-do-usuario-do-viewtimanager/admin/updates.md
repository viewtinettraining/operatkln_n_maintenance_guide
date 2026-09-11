---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Atualizações'
id: QSU-GUJD-JHM-QCI
slug: updates
isVisible: true
isSearchable: true
lastUpdated: '2026-06-12 15:53:47'
---
# **<span align="center">Atualizando a Plataforma e Módulos</span>**

<br />

## **📘 Introdução**

O Viewtinet fornece um mecanismo de atualização integrado que permite aos administradores atualizar toda a plataforma — incluindo todos os seus módulos — para a versão mais recente disponível fornecida pelo Viewtinet.<br />

> ⚠️ **Importante**: Este processo de atualização **aplica-se a toda a plataforma**. **Não é possível atualizar módulos individuais seletivamente** usando este método.

Além do procedimento baseado em GUI descrito nesta seção, as atualizações também podem ser realizadas via linha de comando. Para instruções de atualização baseadas na CLI (Command Line Interface), consulte a seção **"Updating Viewtinet"** no capítulo **"Viewtinet CLI Guide"**.

---

## **📦 Pré-requisitos**

Antes de iniciar o processo de atualização, certifique-se de que os seguintes requisitos sejam atendidos:

-   ✅ Você obteve o **pacote de atualização oficial** (arquivo `.tgz`) com o Viewtinet.
-   ✅ O pacote (bundle) deve ser a versão suportada mais recente, e o link para download será fornecido pela equipe de Suporte do Viewtinet.
-   ✅ Você também deve obter o **arquivo de Senha (Passphrase)** fornecido pela equipe de Suporte do Viewtinet, que é necessário para autenticar a atualização.

### **🔐 Transferindo o Pacote**

1.  Use uma ferramenta compatível com SCP, como **WinSCP**, **FileZilla** ou um terminal com suporte a `scp`, para se conectar ao appliance (servidor ou máquina virtual) do Viewtinet.
2.  Faça login usando um usuário do sistema com permissões de gravação (tipicamente `admin` ou um usuário privilegiado).
3.  Faça o upload do pacote de atualização `.tgz` para o seguinte diretório: `/var/viewtimanager/updates`
    
    <br />
    

### **📂 Extraindo o Pacote**

Assim que o arquivo for carregado com sucesso, você deve extrair seu conteúdo:

1.  Conecte-se ao appliance do Viewtinet via SSH usando o usuário `admin`.
2.  Navegue até o diretório de atualizações:
    
    ```bash
    cd /var/viewtimanager/updates
    ```
    
3.  Descomprima o pacote executando o seguinte comando (substitua `&lt;version&gt;` pelo nome do seu arquivo específico):
    
    ```bash
    tar xvzf bundle-&lt;version&gt;.tgz
    ```
    
4.  Após descomprimir o arquivo, você obterá os arquivos extraídos conforme mostrado abaixo:
    
    <br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-bundle-extracted.png" align="center"></figure>
    
    <br />
    

---

## **Abrir o Gerenciador de Atualizações (Update Manager)**

1.  No menu à esquerda, clique em **Admin**.<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/lIi7e7MEFosaR3xCKoUm.png" align="center"></figure>
    
2.  Selecione a aba **Updates** na parte superior.<br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-tab-new.png" align="center"></figure>
    
    <br />
    

## **Selecionar o Pacote e Atualizar**

1.  Clique na seta suspensa em **Bundles Available** (Pacotes Disponíveis) e selecione o seu pacote.
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-dropdown-new.png" align="center"></figure>
    
    <br />
    
2.  No próximo passo, você deve inserir a frase secreta (passphrase). Após digitá-la, inicie a atualização clicando em **UPDATE**.
    
    <br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-passphrase.png" align="center"></figure>
    
    <br />
    
3.  Por fim, confirme o processo quando solicitado.
    
    <br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-confirm.png" align="center"></figure>
    
    <br />

4.  Durante o processo de instalação, os logs ao vivo serão exibidos como mostrado abaixo:
    
    <br />
    
    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-progress.png" align="center"></figure>
    
    <br />

5.  Uma vez concluído o processo, a saída indicará que a instalação está terminada. Clique no botão **FINISH INSTALLATION** para concluir o processo.
    
    <br />

    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-finished.png" align="center"></figure>

---

## **Reiniciar Cada Módulo**

> **Importante:** Após a atualização, cada módulo deve ser reiniciado para aplicar a nova versão.

1.  No menu à esquerda, vá para **Viewtisight** e reinicie o módulo.
2.  Prossiga com cada módulo ativo (ex: **Viewtilog**, **Viewtimon**, **Viewtify QoS**), dependendo dos seus módulos licenciados.
3.  Para reiniciar um módulo, clique em **RESTART** no canto superior direito e confirme.

    <br />

    <figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/update-restart.png" align="center"></figure>

Repita esse processo para cada módulo ativo até que todos eles estejam executando a versão mais recente.
