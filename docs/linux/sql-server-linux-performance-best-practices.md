---
title: Meilleures pratiques relatives aux performances SQL Server sur Linux
description: Cet article fournit des performances meilleures pratiques et recommandations pour l’exécution de SQL Server sur Linux.
author: rgward
ms.author: bobward
ms.reviewer: vanto
manager: jroth
ms.date: 09/14/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: d82ee87f0911ab6e47a9537e035e522b062a699c
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834848"
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-on-linux"></a>Meilleures pratiques de performances et les instructions de configuration de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article fournit les meilleures pratiques et recommandations pour optimiser les performances pour les applications de base de données qui se connectent à SQL Server sur Linux. Ces recommandations sont spécifiques à l’exécution sur la plateforme Linux. Toutes les recommandations de SQL Server normales, tels que de la conception d’index, s’appliquent toujours.

Les instructions suivantes contiennent des recommandations pour la configuration de SQL Server et le système d’exploitation Linux.

## <a name="sql-server-configuration"></a>Configuration de SQL Server

Il est recommandé d’effectuer les tâches de configuration suivantes après avoir installé SQL Server sur Linux pour obtenir de meilleures performances pour votre application.

### <a name="best-practices"></a>Bonnes pratiques

- **Utiliser l’affinité de processus pour le nœud et/ou de processeurs**

   Il est recommandé d’utiliser `ALTER SERVER CONFIGURATION` pour définir `PROCESS AFFINITY` pour tous les **NUMANODEs** et/ou de l’UC vous utilisez pour SQL Server (qui est généralement utilisé pour tous les nœuds et les unités centrales) sur un système d’exploitation Linux. Affinité du processeur permet de conserver le comportement efficace de Linux et la planification de SQL. À l’aide de la **NUMANODE** option est la méthode la plus simple. Notez que vous devez utiliser **l’affinité de processus** même si vous avez un seul nœud NUMA sur votre ordinateur.  Consultez le [ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md) documentation pour plus d’informations sur la configuration **l’affinité de processus**.

- **Configurer plusieurs fichiers de données tempdb**

   Une installation SQL Server sur Linux n’offre pas une option pour configurer plusieurs fichiers de tempdb, nous recommandons que vous envisagez de créer tempdb plusieurs fichiers de données après l’installation. Pour plus d’informations, consultez les instructions de l’article, [recommandations visant à réduire la contention d’allocation dans la base de données tempdb SQL Server](https://support.microsoft.com/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d).

### <a name="advanced-configuration"></a>Configuration avancée

Les recommandations suivantes sont des paramètres de configuration facultative que vous pouvez choisir d’effectuer après l’installation de SQL Server sur Linux. Ces choix sont basées sur les exigences de votre charge de travail et la configuration de votre système d’exploitation Linux.

- **Définir une limite de mémoire avec mssql-conf**

   Pour assurer la suffisamment de mémoire physique libre pour le système d’exploitation Linux, le processus SQL Server utilise seulement 80 % de la RAM physique par défaut. Pour certains systèmes quelle grande quantité de RAM physique, 20 % peut être un nombre significatif. Par exemple, sur un système avec 1 To de RAM, le paramètre par défaut laissez environ 200 Go de RAM inutilisé. Dans ce cas, vous souhaiterez configurer la limite de mémoire à une valeur plus élevée. Consultez la documentation sur le **mssql-conf** outil et le [memory.memorylimitmb](sql-server-linux-configure-mssql-conf.md#memorylimit) paramètre qui contrôle la mémoire visible pour SQL Server (en unités de Mo).

   Lorsque vous modifiez ce paramètre, veillez à ne pas définir cette valeur trop élevée. Si vous ne conservez pas suffisamment de mémoire, vous pouvez rencontrer des problèmes avec le système d’exploitation Linux et d’autres applications de Linux.

## <a name="linux-os-configuration"></a>Configuration du système d’exploitation Linux

Envisagez d’utiliser les paramètres de configuration de système d’exploitation Linux suivants pour découvrir les meilleures performances pour une Installation SQL Server.

### <a name="kernel-settings-for-high-performance"></a>Paramètres de noyau pour de hautes performances
Il s’agit de la performance associés à haute des paramètres de système d’exploitation Linux et du débit pour une installation de SQL Server recommandée. Consultez la documentation de votre système d’exploitation Linux pour le processus configurer ces paramètres.



> [!Note]
> Pour les utilisateurs de Red Hat Enterprise Linux (RHEL), le profil de performances de débit configurera ces paramètres automatiquement (à l’exception des États-C).

Le tableau suivant fournit des recommandations pour les paramètres de l’UC :

| Paramètre | Value | Plus d’informations |
|---|---|---|
| Gouverneur de fréquence du processeur | performances | Consultez le **cpupower** commande |
| ENERGY_PERF_BIAS | performances | Consultez le **x86_energy_perf_policy** commande |
| min_perf_pct | 100 | Consultez votre documentation sur intel p-état |
| États C | C1 uniquement | Consultez la documentation de votre système Linux ou et vous assurer que les États C a la valeur C1 uniquement |

Le tableau suivant fournit des recommandations pour les paramètres de disque :

| Paramètre | Value | Plus d’informations |
|---|---|---|
| anticipation de disque | 4096 | Consultez le **blockdev** commande |
| paramètres de sysctl | kernel.sched_min_granularity_ns = 10000000<br/>kernel.sched_wakeup_granularity_ns = 15000000<br/>vm.dirty_ratio = 40<br/>vm.dirty_background_ratio = 10<br/>vm.swappiness=10 | Consultez le **sysctl** commande |

### <a name="kernel-setting-auto-numa-balancing-for-multi-node-numa-systems"></a>Noyau paramètre automatique numa équilibrage pour les systèmes à plusieurs nœuds NUMA

Si vous installez SQL Server sur un nœud multi **NUMA** systèmes, ce qui suit **kernel.numa_balancing** paramètre de noyau est activé par défaut. Pour permettre à SQL Server fonctionner à l’efficacité maximale sur un **NUMA** système, désactiver auto numa équilibrage sur un système NUMA de plusieurs nœuds :

```bash
sysctl -w kernel.numa_balancing=0
```

### <a name="kernel-settings-for-virtual-address-space"></a>Paramètres de noyau pour l’espace d’adressage virtuel

Le paramètre par défaut **vm.max_map_count** (qui est de 65536) est peut-être pas suffisamment élevée pour une installation de SQL Server. Modifiez cette valeur (qui est une limite supérieure) à 256 Ko.

```bash
sysctl -w vm.max_map_count=262144
```

### <a name="disable-last-accessed-datetime-on-file-systems-for-sql-server-data-and-log-files"></a>Désactiver la date/date du dernier accès sur les systèmes de fichiers pour les fichiers journaux et de données SQL Server

Utilisez le **noatime** attribut avec n’importe quel système de fichiers qui est utilisé pour stocker les données de SQL Server et les fichiers journaux. Consultez votre documentation Linux sur la façon de définir cet attribut.

### <a name="leave-transparent-huge-pages-thp-enabled"></a>Laissez Transparent énorme Pages (THP) activé

La plupart des installations de Linux doit avoir cette option sur par défaut. Nous recommandons pour l’expérience de performances plus cohérente de laisser cette option de configuration est activée.

### <a name="swapfile"></a>swapfile

Assurez-vous de qu'avoir un fichier d’échange configuré correctement pour éviter les problèmes de mémoire insuffisante. Consultez votre documentation Linux pour savoir comment créer et dimensionner correctement un fichier d’échange.

### <a name="virtual-machines-and-dynamic-memory"></a>Machines virtuelles et la mémoire dynamique

Si vous exécutez SQL Server sur Linux dans une machine virtuelle, veillez à que sélectionner les options pour résoudre la quantité de mémoire réservée pour la machine virtuelle. N’utilisez pas de fonctionnalités telles que la mémoire dynamique Hyper-V.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les fonctionnalités de SQL Server qui améliorent les performances, consultez [prise en main des fonctionnalités de performances](sql-server-linux-performance-get-started.md).

Pour plus d’informations sur SQL Server sur Linux, consultez [vue d’ensemble de SQL Server sur Linux](sql-server-linux-overview.md).
