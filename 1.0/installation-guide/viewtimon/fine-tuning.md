---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Fine Tuning'
id: JB9-WUEB-9W1-SFX
slug: fine-tuning
isVisible: true
lastUpdated: '2025-10-15 10:28:49'
---
# **<span align="center">Ajuste Fino para Desempenho do Viewtimon</span>**

Para maximizar o throughput, minimizar a latência e garantir uma operação confiável, aplique os seguintes ajustes de kernel e nível de sistema em cada host do Viewtimon.

<br />

## **Temporizador de Eventos de Alta Precisão (HPET)**

O HPET fornece timestamps de alta resolução para captura de pacotes e agendamento:

1.  **Verificar suporte**
    
    ```bash
    cat /sys/devices/system/clocksource/clocksource0/available_clocksource
    # ex: tsc hpet acpi_pm
    ```
    
2.  **Se** `hpet` aparecer, habilite-o no GRUB:
    
    -   Edite `/etc/default/grub`
    -   Adicione `clocksource=hpet` em `GRUB_CMDLINE_LINUX_DEFAULT`:
        
        ```diff
        --- /etc/default/grub
        + GRUB_CMDLINE_LINUX_DEFAULT="… clocksource=hpet"
        ```
        
3.  **Atualizar o GRUB** e reiniciar:
    
    ```bash
    sudo update-grub
    sudo reboot
    ```
    

---

## **Hugepages**

Alocar páginas grandes (hugepages) reduz a sobrecarga da TLB e aumenta o desempenho da memória.

<br />

### **A. Hugepages de 1 GB (Recomendado)**

1.  **Verificar suporte**
    
    ```bash
    cat /proc/cpuinfo | egrep -o pdpe1gb | head -n1
    # retorna pdpe1gb se suportado
    ```
    
2.  **Determinar a quantidade** com base nos nós NUMA e na RAM:
    
    <table><tbody><tr><th><p>Nós NUMA</p></th><th><p>RAM</p></th><th><p>Hugepages</p></th></tr><tr><td><p>1</p></td><td><p>128 GB</p></td><td><p>32</p></td></tr><tr><td><p>1</p></td><td><p>96 GB</p></td><td><p>24</p></td></tr><tr><td><p>1</p></td><td><p>64 GB</p></td><td><p>16</p></td></tr><tr><td><p>1</p></td><td><p>32 GB</p></td><td><p>8</p></td></tr><tr><td><p>2</p></td><td><p>128 GB</p></td><td><p>32</p></td></tr><tr><td><p>2</p></td><td><p>96 GB</p></td><td><p>32</p></td></tr><tr><td><p>2</p></td><td><p>64 GB</p></td><td><p>24</p></td></tr><tr><td><p>2</p></td><td><p>32 GB</p></td><td><p>16</p></td></tr></tbody></table>
    
3.  **Habilitar no GRUB** (exemplo: 1 NUMA, 128 GB → 48 páginas):
    
    ```diff
    --- /etc/default/grub
    + GRUB_CMDLINE_LINUX_DEFAULT="… default_hugepagesz=1G hugepagesz=1G hugepages=48"
    ```
    
4.  **Atualizar o GRUB**:
    
    ```bash
    sudo update-grub
    ```
    
5.  **Montar o sistema de arquivos hugepage**:
    
    ```bash
    echo "nodev /mnt/huge_1GB hugetlbfs pagesize=1GB 0 0" | sudo tee -a /etc/fstab
    sudo mkdir -p /mnt/huge_1GB
    sudo mount -a
    ```
    

> **Notas:**
> 
> -   Recomenda-se fortemente um servidor de nó único NUMA.
> -   Em servidores de nó duplo NUMA, o sistema operacional liberará metade das páginas do nó 2 no tempo de execução se elas não forem usadas.

<br />

### **B. Hugepages de 2 MB (Alternativa)**

<br />

1.  **Verificar suporte**
    
    ```bash
    cat /proc/cpuinfo | egrep -o pse | head -n1
    # retorna pse se suportado
    ```
    
2.  **Montar e configurar**:
    
    ```bash
    echo "nodev /mnt/huge hugetlbfs defaults 0 0" | sudo tee -a /etc/fstab
    sudo mkdir -p /mnt/huge
    echo "vm.nr_hugepages = X" | sudo tee -a /etc/sysctl.conf
    sudo mount -a
    sudo sysctl -p
    ```
    
    Substitua `X` pelo número desejado de páginas de 2 MB.
    

---

## **Configuração de Alto Desempenho do Viewtimon**

### **Isolamento de CPU**

Evite que outros processos disputem recursos com o Viewtimon:

1.  **Calcular as CPUs a isolar**:
    
    ```bash
    STAGES=$(grep -c '^stage' /opt/vn/config/viewtimon/etc/pipeline.cfg)
    ANALYZE=$(grep -A1 '^stage' /opt/vn/config/viewtimon/etc/pipeline.cfg               | grep -c '= analyze')
    CPUS=$((STAGES + ANALYZE + 2))   # +1 master +1 bypasser
    echo "Isolate $CPUS CPUs"
    ```
    
    Ou execute o script auxiliar:
    
    ```bash
    sudo /opt/vn/viewtinet-builder/scripts/compute-isolated-cpus.sh
    ```
    
2.  **Editar o GRUB** (exemplo: isolar as CPUs 3–6):
    
    ```diff
    --- /etc/default/grub
    + GRUB_CMDLINE_LINUX_DEFAULT="… isolcpus=3-6 nohz_full=3-6 rcu_nocbs=3-6 nohz=on"
    ```
    
3.  **(Apenas AMD)** adicione:
    
    ```diff
    + iommu=pt amd_iommu=on
    ```
    
4.  **Aplicar as alterações**:
    
    ```bash
    sudo update-grub
    ```
    

### **Configuração de Desempenho da CPU**

Desabilite as mitigações Spectre/Meltdown em ambientes confiáveis:

```diff
--- /etc/default/grub
+ GRUB_CMDLINE_LINUX_DEFAULT="… mitigations=off"
```

```bash
sudo update-grub
```

---

> **Etapa Final:**<br />
> Reinicie o servidor para aplicar todos os parâmetros de kernel e montagens:
> 
> ```bash
> sudo reboot
> ```

<br />