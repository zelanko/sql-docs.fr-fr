---
title: Meilleures pratiques en matière de performances pour SQL Server sur Linux
description: Cet article fournit les meilleures pratiques en matière de performances et des lignes directrices sur l’exécution de SQL Server sur Linux.
author: tejasaks
ms.author: tejasaks
ms.reviewer: vanto
ms.date: 09/16/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 1b2a4f55908f249d9f574d392dea26932648e58d
ms.sourcegitcommit: c74bb5944994e34b102615b592fdaabe54713047
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90989912"
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-on-linux"></a>Meilleures pratiques en matière de performances et lignes directrices de configuration pour SQL Server sur Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Cet article présente les meilleures pratiques et suggestions pour optimiser les performances des applications de base de données qui se connectent à SQL Server sur Linux. Ces suggestions sont spécifiques à l’exécution sur la plateforme Linux. Toutes les suggestions de SQL Server normales, telles que la conception d’index, s’appliquent toujours.

Les lignes directrices suivantes contiennent des suggestions de configuration de SQL Server et du système d’exploitation Linux.

## <a name="sql-server-configuration"></a>Configuration de SQL Server

Il est recommandé d’effectuer les tâches de configuration suivantes après avoir installé SQL Server sur Linux pour obtenir les meilleures performances pour votre application.

### <a name="best-practices"></a>Meilleures pratiques

- **Utiliser PROCESS AFFINITY pour le nœud et/ou les UC**

   Il est recommandé d’utiliser `ALTER SERVER CONFIGURATION` pour définir `PROCESS AFFINITY` pour tous les **NUMANODE** et/ou les UC que vous utilisez pour SQL Server (généralement pour tous les nœuds et toutes les UC) sur un système d’exploitation Linux. L’affinité du processus permet de conserver un comportement de planification Linux et SQL efficace. L’utilisation de l’option **NUMANODE** est la méthode la plus simple. Notez que vous devez utiliser **PROCESS AFFINITY** même si vous n’avez qu’un seul nœud NUMA sur votre ordinateur.  Consultez la documentation [ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md) documentation for more information on how to set **PROCESS AFFINITY**.

- **Configurer plusieurs fichiers de données tempdb**

   Étant donné qu’une installation SQL Server sur Linux ne propose pas d’option de configuration de plusieurs fichiers tempdb, nous vous recommandons de considérer la création de plusieurs fichiers de données tempdb après l’installation. Pour plus d’informations, reportez-vous aux instructions de l’article [Suggestions pour réduire la contention d’allocation dans la base de données tempdb SQL Server](https://support.microsoft.com/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d).

### <a name="advanced-configuration"></a>Configuration avancée

Les suggestions suivantes sont des paramètres de configuration facultatifs que vous pouvez choisir d’effectuer après l’installation de SQL Server sur Linux. Ces choix sont basés sur les exigences de votre charge de travail et de la configuration de votre système d’exploitation Linux.

- **Définir une limite de mémoire avec mssql-conf**

   Pour garantir qu’il y a suffisamment de mémoire physique libre pour le système d’exploitation Linux, le processus de SQL Server utilise uniquement 80 % de RAM physique par défaut. Pour certains systèmes qui ont une grande quantité de RAM physique, 20 % peut être un nombre significatif. Par exemple, sur un système avec 1 To de RAM, le paramètre par défaut laisse environ 200 Go de RAM inutilisée. Dans ce cas, vous souhaiterez peut-être configurer la limite de la mémoire sur une valeur plus élevée. Consultez la documentation sur l'outil **mssql-conf** et le paramètre [memory.memorylimitmb](sql-server-linux-configure-mssql-conf.md#memorylimit) qui contrôle la mémoire visible pour SQL Server (en mégaoctets).

   Lorsque vous modifiez ce paramètre, veillez à ne pas définir cette valeur trop élevée. Si vous ne laissez pas suffisamment de mémoire, vous risquez de rencontrer des problèmes avec le système d’exploitation Linux et d’autres applications Linux.

## <a name="linux-os-configuration"></a>Configuration du système d'exploitation Linux

Envisagez d’utiliser les paramètres de configuration du système d’exploitation Linux suivants pour bénéficier des meilleures performances pour une installation SQL Server.

### <a name="kernel-settings-for-high-performance"></a>Paramètres du noyau pour de hautes performances
Il s’agit des paramètres de système d’exploitation Linux recommandés en rapport avec la haute performance et le débit d’une installation SQL Server. Consultez la documentation sur le système d'exploitation Linux relative au processus de configuration de ces paramètres.



> [!Note]
> Pour les utilisateurs de Red Hat Enterprise Linux (RHEL), le profil débit-performance [Tuned](https://tuned-project.org) configure automatiquement ces paramètres (à l’exception des États C). À partir de RHEL 8.0, un profil MSSQL intégré /usr/lib/tuned codéveloppé avec Red Hat offre des réglages de performances Linux plus fins pour les charges de travail SQL Server. Ce profil inclut le profil débit-performance RHEL. Vous trouverez ses définitions ci-après ainsi que d’autres distributions Linux et versions de RHEL sans ce profil.

La table suivante fournit des suggestions pour les paramètres de l’UC :

| Paramètre | Valeur | Informations complémentaires |
|---|---|---|
| Gouverneur de fréquence de l’UC | performances | Consultez la commande **cpupower** |
| ENERGY_PERF_BIAS | performances | Consultez la commande **x86_energy_perf_policy** |
| min_perf_pct | 100 | Consultez votre documentation sur l’état P Intel |
| États C | C1 uniquement | Consultez la documentation Linux ou de votre système pour savoir comment garantir que les états C sont définis sur C1 uniquement |

La table suivante fournit des suggestions pour les paramètres du disque :

| Paramètre | Valeur | Informations complémentaires |
|---|---|---|
| Lecture anticipée du disque | 4096 | Consultez la commande **blockdev** |
| paramètres sysctl | kernel.sched_min_granularity_ns = 10000000<br/>kernel.sched_wakeup_granularity_ns = 15000000<br/>vm.dirty_ratio = 40<br/>vm.dirty_background_ratio = 10<br/>vm.swappiness = 10 | Consultez la commande **sysctl** |

### <a name="kernel-setting-auto-numa-balancing-for-multi-node-numa-systems"></a>Paramètre de noyau d’équilibrage NUMA automatique pour les systèmes NUMA à plusieurs nœuds

Si vous installez SQL Server sur des systèmes **NUMA** à plusieurs nœuds, le paramètre de noyau **kernel. numa_balancing** suivant est activé par défaut. Pour permettre à SQL Server de fonctionner avec un niveau d'efficacité maximal sur un système **NUMA**, désactivez l’équilibrage NUMA automatique sur un système NUMA à plusieurs nœuds :

```bash
sysctl -w kernel.numa_balancing=0
```

### <a name="kernel-settings-for-virtual-address-space"></a>Paramètres de noyau pour l’espace d’adressage virtuel

La valeur par défaut de **vm. max _map_count** (65536) peut ne pas être suffisamment élevée pour une installation SQL Server. Pour cette raison, remplacez la valeur de **vm.max_map_count** par 262144 pour un déploiement SQL Server, et reportez-vous à la section [Paramètres Linux proposés à l’aide d’un profil MSSQL optimisé](#proposed-linux-settings-using-a-tuned-mssql-profile) pour affiner les paramètres de ce noyau. La valeur maximale pour vm.max_map_count est 2147483647.

```bash
sysctl -w vm.max_map_count=262144
```

### <a name="proposed-linux-settings-using-a-tuned-mssql-profile"></a>Paramètres Linux proposés avec un profil MSSQL Tuned

```bash
#
# A tuned configuration for SQL Server on Linux
#
    
[main]
summary=Optimize for Microsoft SQL Server
include=throughput-performance
    
[cpu]
force_latency=5

[sysctl]
vm.swappiness = 1
vm.dirty_background_ratio = 3
vm.dirty_ratio = 80
vm.dirty_expire_centisecs = 500
vm.dirty_writeback_centisecs = 100
vm.transparent_hugepages=always
# For multi-instance SQL deployments, use
# vm.transparent_hugepages=madvice
vm.max_map_count=1600000
net.core.rmem_default = 262144
net.core.rmem_max = 4194304
net.core.wmem_default = 262144
net.core.wmem_max = 1048576
kernel.numa_balancing=0
kernel.sched_latency_ns = 60000000
kernel.sched_migration_cost_ns = 500000
kernel.sched_min_granularity_ns = 15000000
kernel.sched_wakeup_granularity_ns = 2000000
```

Pour activer ce profil Tuned, enregistrez ces définitions dans un fichier **tuned.conf** dans un dossier /usr/lib/tuned/mssql et activez le profil en utilisant

```bash
chmod +x /usr/lib/tuned/mssql/tuned.conf
tuned-adm profile mssql
```

Vérifiez son activation avec

```bash
tuned-adm active
```
or
```bash
tuned-adm list
```

### <a name="disable-last-accessed-datetime-on-file-systems-for-sql-server-data-and-log-files"></a>Désactiver la date/heure du dernier accès aux systèmes de fichiers pour les données et les fichiers journaux SQL Server

Utilisez l'attribut **noatime** avec tout système de fichiers utilisé pour stocker les données et les fichiers journaux SQL Server. Reportez-vous à la documentation Linux pour savoir comment définir cet attribut.

### <a name="leave-transparent-huge-pages-thp-enabled"></a>Laissez les pages volumineuses transparentes (THP) activées

Cette option doit être activée par défaut pour la plupart des installations Linux. Nous vous recommandons d’utiliser les performances les plus cohérentes pour garder cette option de configuration activée. Toutefois, en cas d’activité de pagination sollicitant une grande quantité de mémoire (par exemple, dans le cadre de déploiements SQL Server avec plusieurs instances ou d’une exécution de SQL Server avec d’autres applications nécessitant une grande quantité de mémoire sur le serveur), nous vous suggérons de tester les performances de vos applications après l’exécution de la commande 

```bash
echo madvise > /sys/kernel/mm/transparent_hugepage/enabled
```
ou en modifiant le profil MSSQL Tuned avec la ligne

```bash
vm.transparent_hugepages=madvise
```
et en activant le profil MSSQL après la modification
```bash
tuned-adm off
tuned-adm profile mssql
```

### <a name="swapfile"></a>fichier d’échange

Vérifiez que vous disposez d’un fichier d’échange correctement configuré pour éviter les problèmes de mémoire insuffisante. Consultez la documentation Linux pour savoir comment créer et dimensionner correctement un fichier d’échange.

### <a name="virtual-machines-and-dynamic-memory"></a>Machines virtuelles et mémoire dynamique

Si vous exécutez SQL Server sur Linux sur une machine virtuelle, assurez-vous de sélectionner des options pour corriger la quantité de mémoire réservée pour la machine virtuelle. N’utilisez pas de fonctionnalités comme Mémoire dynamique Hyper-V.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les fonctionnalités de SQL Server qui améliorent les performances, consultez [Prise en main des fonctionnalités de performances](sql-server-linux-performance-get-started.md).

Pour plus d’informations sur SQL Server sur Linux, consultez [Vue d’ensemble de SQL Server sur Linux](sql-server-linux-overview.md).
