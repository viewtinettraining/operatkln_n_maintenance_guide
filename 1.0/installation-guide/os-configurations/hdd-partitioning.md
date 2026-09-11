---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Particionamento de Disco (HDD)'
id: BGW-74PL-76T-ZMH
slug: hdd-partitioning
isVisible: true
lastUpdated: '2025-10-15 10:54:43'
---
# **<span align="center">Particionamento de HDD</span>**

<br />

## **Esquema de Particionamento Recomendado**

A Viewtinet recomenda fortemente que as instalações utilizem **dois grupos separados de discos** para desempenho e redundância ideais:

-   **Primeiro Grupo de Discos (Sistema Operacional):** Use uma configuração RAID 1 com pelo menos **2 discos físicos** para proteger os dados do sistema operacional.
-   **Segundo Grupo de Discos (Data Warehouse):** Use pelo menos **2 discos físicos adicionais**. Dependendo do número de discos disponíveis, sugere-se implementar RAID 10 (preferencialmente) ou RAID 5.

Para servidores equipados com controladores RAID físicos, configure os arrays RAID diretamente no controlador.

<br />

### **Partições Recomendadas para o Sistema Operacional (Grupo de Discos 1 - RAID 1):**

<table><tbody><tr><th><p>Ponto de Montagem</p></th><th><p>Tamanho Recomendado</p></th><th><p>Tipo de Partição</p></th><th><p>Sistema de Arquivos</p></th></tr><tr><td><p><code>/boot</code></p></td><td><p>1 GB</p></td><td><p>Primária</p></td><td><p>XFS</p></td></tr><tr><td><p><code>swap</code></p></td><td><p>96 GB (ou o mesmo valor da RAM)</p></td><td><p>Primária</p></td><td><p>swap</p></td></tr><tr><td><p><code>/</code></p></td><td><p>35 GB</p></td><td><p>Lógica</p></td><td><p>XFS</p></td></tr><tr><td><p><code>/home</code></p></td><td><p>50 GB</p></td><td><p>Lógica</p></td><td><p>XFS</p></td></tr><tr><td><p><code>/tmp</code></p></td><td><p>10 GB</p></td><td><p>Lógica</p></td><td><p>XFS</p></td></tr><tr><td><p><code>/var</code></p></td><td><p>100 GB</p></td><td><p>Lógica</p></td><td><p>XFS</p></td></tr></tbody></table>

<br />

### **Partições Recomendadas para o Data Warehouse (Grupo de Discos 2 - RAID 10 preferencial ou RAID 5):**

<table><tbody><tr><th><p>Ponto de Montagem</p></th><th><p>Tamanho Recomendado</p></th><th><p>Tipo de Partição</p></th><th><p>Sistema de Arquivos</p></th><th><p>Comentários</p></th></tr><tr><td><p><code>/opt/vn</code></p></td><td><p>200 GB</p></td><td><p>Lógica</p></td><td><p>ext4</p></td><td><p><br></p></td></tr><tr><td><p><code>/opt/vn/viewticore/</code></p></td><td><p>1.2 TB</p></td><td><p>Lógica</p></td><td><p>ext4</p></td><td><p><br></p></td></tr><tr><td><p><code>/opt/vn/dhyana/var/data/</code></p></td><td><p>400 GB</p></td><td><p>Lógica</p></td><td><p>ext4</p></td><td><p>Ou aumente se mais espaço estiver disponível</p></td></tr><tr><td><p><code>/opt/vn/probe/var/</code><br>(se o viewtimon for implantado)</p></td><td><p>600 GB</p></td><td><p>Lógica</p></td><td><p>ext4</p></td><td><p>Ou aumente se mais espaço estiver disponível</p></td></tr></tbody></table>

-   **Nota:** Ajuste os tamanhos das partições proporcionalmente de acordo com suas necessidades específicas e capacidade de disco disponível.

---

## **Recomendações para Discos NVMe**

Para servidores equipados com discos NVMe que não possuem um controlador RAID físico, configure as partições usando o utilitário RAID por software do Linux (mdadm):

-   Use RAID 1 para as partições do Sistema Operacional.
-   Use RAID 10 (preferencialmente) ou RAID 5 para as partições do Data Warehouse.

---

## **Recomendações para Máquinas Virtuais**

Em ambientes virtualizados, a Viewtinet recomenda manter a mesma separação lógica:

-   Use **dois armazenamentos virtuais separados**:
    
    -   Um disco virtual dedicado às partições do sistema operacional.
    -   Um ou mais discos virtuais para o armazenamento do Data Warehouse.

Essa configuração mantém a separação e garante desempenho e capacidade de gerenciamento ideais.

---

## **Personalizando o Particionamento Durante a Instalação**

Durante a instalação do Ubuntu Server, selecione **Custom storage layout** (Layout de armazenamento personalizado) para definir manualmente as partições de acordo com as diretrizes fornecidas acima. Certifique-se de que os sistemas de arquivos corretos e as configurações de RAID sejam aplicadas com base em seu ambiente (controlador RAID físico, discos NVMe ou ambiente virtualizado).

---

**Importante:**

-   A configuração do particionamento deve ser concluída **antes** de prosseguir com as etapas de instalação do Viewtinet descritas posteriormente neste manual.
-   Instruções detalhadas para o particionamento de disco além destas diretrizes estão fora do escopo deste documento.

<br />

<br />

<br />