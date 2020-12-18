---
title: Meilleures pratiques en matière de performances pour SQL Server sur Linux
description: Cet article présente les bonnes pratiques en matière de performances et les instructions d’exécution de SQL Server sur Linux.
author: tejasaks
ms.author: tejasaks
ms.reviewer: vanto
ms.date: 12/11/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 89b8a7c087fb87ed911be640126ec81021b045a7
ms.sourcegitcommit: 2991ad5324601c8618739915aec9b184a8a49c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323373"
---
# <a name="performance-best-practices-and-configuration-guidelines-for-sql-server-on-linux"></a>Meilleures pratiques en matière de performances et lignes directrices de configuration pour SQL Server sur Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Cet article présente les meilleures pratiques et suggestions pour optimiser les performances des applications de base de données qui se connectent à SQL Server sur Linux. Ces suggestions sont spécifiques à l’exécution sur la plateforme Linux. Toutes les suggestions de SQL Server normales, telles que la conception d’index, s’appliquent toujours.

Les directives suivantes contiennent des suggestions de configuration de SQL Server et du système d’exploitation Linux.

## <a name="linux-os-configuration"></a>Configuration du système d'exploitation Linux

Envisagez d’utiliser les paramètres de configuration suivants du système d’exploitation Linux pour bénéficier des meilleures performances pour une installation SQL Server.

### <a name="storage-configuration-recommendation"></a>Configuration de stockage recommandée

#### <a name="use-storage-subsystem-with-appropriate-iops-throughput-and-redundancy"></a>Utiliser le sous-système de stockage avec les E/S par seconde, le débit et la redondance appropriés

Le sous-système de stockage qui héberge des données, des journaux de transactions et d’autres fichiers associés (tels que les fichiers de point de contrôle pour OLTP en mémoire) doit être capable de gérer de manière appropriée des charges de travail moyennes et maximales. Normalement, dans des environnements locaux, le fournisseur de stockage prend en charge la configuration RAID matérielle appropriée avec agrégation par bandes sur plusieurs disques pour garantir des E/S par seconde, un débit et une redondance appropriés. Toutefois, cela peut varier selon les fournisseurs de stockage et les offres de stockage aux architectures variées.

Pour un déploiement de SQL Server sur Linux sur des machines virtuelles Azure, envisagez d’utiliser un RAID logiciel pour répondre aux besoins d’E/S par seconde et de débit. Reportez-vous à l’article suivant lors de la configuration de SQL Server sur des machines virtuelles Azure pour des considérations de stockage similaires : [Configuration du stockage pour les machines virtuelles SQL Server](https://docs.microsoft.com/azure/azure-sql/virtual-machines/windows/storage-configuration)

Un exemple de création d’un RAID logiciel dans Linux sur des machines virtuelles Azure est présenté ci-dessous. Toutefois, vous devez utiliser le nombre approprié de disques de données pour le débit et les E/S par seconde requis pour les volumes, selon les exigences relatives aux données, aux journaux de transactions et aux E/S de tempdb. Dans cet exemple, huit disques de données ont été attachés à la machine virtuelle Azure : 4 pour héberger les fichiers de données, 2 pour les journaux des transactions et 2 pour la charge de travail tempdb.

```bash
# To locate the devices (for example /dev/sdc) for RAID creation, use the lsblk command
# For Data volume, using 4 devices, in RAID 5 configuration with 8KB stripes
mdadm --create --verbose /dev/md0 --level=raid5 --chunk=8K --raid-devices=4 /dev/sdc /dev/sdd /dev/sde /dev/sdf

# For Log volume, using 2 devices in RAID 10 configuration with 64KB stripes
mdadm --create --verbose /dev/md1 --level=raid10 --chunk=64K --raid-devices=2 /dev/sdg /dev/sdh

# For tempdb volume, using 2 devices in RAID 0 configuration with 64KB stripes
mdadm --create --verbose /dev/md2 --level=raid0 --chunk=64K --raid-devices=2 /dev/sdi /dev/sdj
```

#### <a name="file-system-configuration-recommendation"></a>Configuration recommandée du système de fichiers

SQL Server prend en charge les systèmes de fichiers EXT4 et XFS pour héberger la base de données, les journaux des transactions et des fichiers supplémentaires, tels que les fichiers de point de contrôle pour OLTP en mémoire dans SQL Server. Microsoft recommande d’utiliser le système de fichiers XFS pour héberger les fichiers de données et les fichiers journaux de transactions SQL Server.

```bash
# Formatting the volume with XFS filesystem
mkfs.xfs /dev/md0 -f -L datavolume
mkfs.xfs /dev/md1 -f -L logvolume
mkfs.xfs /dev/md2 -f -L tempdb
```

> [!NOTE]
> Il est possible de configurer le système de fichiers XFS pour qu’il ne prenne pas en compte la casse lors de la création et de la mise en forme du volume XFS. Ce n’est pas une configuration fréquemment utilisée dans l’écosystème Linux, mais elle peut être utilisée pour des raisons de compatibilité.
>
> Exemple : mkfs.xfs /dev/md0 -f -n version=ci -L datavolume
>
> Dans cet exemple, les paramètres `-n version=ci` configurent le système de fichiers XFS pour qu’il ne prenne pas en compte la casse.

##### <a name="persistent-memory-filesystem-recommendation"></a>Système de fichiers de mémoire persistante recommandé

Pour la configuration du système de fichiers sur les appareils à mémoire persistante, l’allocation de blocs pour le système de fichiers sous-jacent doit être de 2 Mo. Pour plus d’informations à ce sujet, consultez l’article [Considérations techniques](sql-server-linux-configure-pmem.md#technical-considerations).

#### <a name="disable-last-accessed-datetime-on-file-systems-for-sql-server-data-and-log-files"></a>Désactiver la date/heure du dernier accès aux systèmes de fichiers pour les données et les fichiers journaux SQL Server

Pour vous assurer que le ou les lecteurs attachés au système sont remontés automatiquement après un redémarrage, ils doivent être ajoutés au fichier `/etc/fstab`. Il est également vivement recommandé d’utiliser l’UUID (identificateur unique universel) dans `/etc/fstab` pour faire référence au lecteur plutôt que d’utiliser uniquement le nom de l’appareil (tel que `/dev/sdc1`).

Il est fortement recommandé d’utiliser l’attribut **noatime** avec tout système de fichiers servant à stocker des données et des fichiers journaux SQL Server. Reportez-vous à la documentation Linux pour savoir comment définir cet attribut. Vous trouverez ci-dessous un exemple illustrant comment activer l’option **noatime** pour un volume monté dans une machine virtuelle Azure.

L’entrée du point de montage est **_/etc/fstab_* _

```bash
UUID="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" /data1 xfs,rw,attr2,noatime 0 0
```

Dans l’exemple ci-dessus, l’UUID représente l’appareil que vous pouvez trouver à l’aide de la commande _*_blkid_*_.

#### <a name="sql-server-and-forced-unit-access-fua-io-subsystem-capability"></a>Fonctionnalité du sous-système d’E/S SQL Server et FUA (Forced Unit Access)

Certaines versions des distributions Linux prises en charge fournissent une prise en charge permettant à la fonctionnalité du sous-système d’E/S FUA d’assurer la durabilité des données. SQL Server utilise la fonctionnalité FUA pour fournir des E/S hautement efficaces et fiables pour la charge de travail SQL Server. Pour plus d’informations sur la prise en charge de FUA par la distribution Linux et son impact pour SQL Server, consultez le blog suivant : [SQL Server On Linux: Forced Unit Access (FUA) Internals](https://bobsql.com/sql-server-on-linux-forced-unit-access-fua-internals/)

SUSE Linux Enterprise Server 12 SP5 et Red Hat Enterprise Linux 8.0 (et versions ultérieures) prennent en charge la fonctionnalité FUA dans le sous-système d’E/S. Si vous utilisez SQL Server 2017 CU6 et versions ultérieures ou SQL Server 2019, vous devez utiliser la configuration suivante pour assurer l’implémentation d’E/S efficace et performante avec FUA par SQL Server.

Utilisez la configuration recommandée listée ci-dessous si les conditions suivantes sont remplies.

- Utilisation de SQL Server 2017 CU6 ou version ultérieure, ou de SQL Server 2019
- Utilisation d’une distribution Linux et d’une version prenant en charge la fonctionnalité FUA (Red Hat Enterprise Linux 8.0 ou version ultérieure, ou SUSE Linux Enterprise Server 12 SP5)
- Sous-système de stockage et/ou matériel prenant en charge la fonctionnalité FUA et configuré pour celle-ci

Configuration recommandée :

1. Activez l’indicateur de trace 3979 en tant que paramètre de démarrage.
2. Utilisez _ *mssql-conf** pour configurer `control.writethrough = 1` et `control.alternatewritethrough = 0`.

Pour presque toutes les autres configurations qui ne respectent pas les conditions précédentes, la configuration recommandée est la suivante :

1. Activez l’indicateur de trace 3982 en tant que paramètre de démarrage (par défaut pour SQL Server dans l’écosystème Linux), tout en veillant à ce que l’indicateur de trace 3979 ne soit pas activé en tant que paramètre de démarrage.
2. Utilisez **mssql-conf** pour configurer `control.writethrough = 1` et `control.alternatewritethrough = 1`.

### <a name="kernel-and-cpu-settings-for-high-performance"></a>Paramètres de noyau et de processeur pour une haute performance

La section suivante décrit les paramètres de système d’exploitation Linux recommandés en rapport avec la haute performance et le débit d’une installation SQL Server. Reportez-vous à la documentation sur le système d’exploitation Linux pour consulter le processus de configuration de ces paramètres. L’utilisation de [**_Tuned_* _](https://tuned-project.org), telle qu’elle est décrite, aide à configurer de nombreux processeurs et à effectuer les configurations de noyau décrites ci-dessous.

#### <a name="using-__tuned__-to-configure-kernel-settings"></a>Utilisation de _*_Tuned_*_ pour configurer les paramètres de noyau

Pour les utilisateurs de Red Hat Enterprise Linux (RHEL), le profil débit-performance [Tuned](https://tuned-project.org) configure automatiquement certains paramètres de noyau et de processeur (à l’exception des états C). À partir de RHEL 8.0, un profil _*_Tuned_*_ nommé _ *mssql** a été codéveloppé avec Red Hat et offre des réglages de performances Linux plus précis pour les charges de travail SQL Server. Ce profil inclut le profil débit-performance RHEL. Vous trouverez ses définitions ci-après ainsi que d’autres distributions Linux et versions de RHEL sans ce profil.

Pour SUSE Linux Enterprise Server 12 SP5, Ubuntu 18.04 et Red Hat Enterprise Linux 7.x, le package **_Tuned_ *_ peut être installé manuellement. Il peut être utilisé pour créer et configurer le profil _* mssql** comme décrit ci-dessous.

##### <a name="proposed-linux-settings-using-a-tuned-mssql-profile"></a>Paramètres Linux proposés avec un profil mssql Tuned

```bash
#
# A Tuned configuration for SQL Server on Linux
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
# vm.transparent_hugepages=madvise
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

Pour activer ce profil Tuned, enregistrez ces définitions dans un fichier **tuned.conf**, dans un dossier `/usr/lib/tuned/mssql`, et activez le profil en utilisant les commandes suivantes :

```bash
chmod +x /usr/lib/tuned/mssql/tuned.conf
tuned-adm profile mssql
```

Vérifiez qu’il est activé à l’aide de la commande suivante :

```bash
tuned-adm active
```

ou

```bash
tuned-adm list
```

#### <a name="cpu-settings-recommendation"></a>Recommandation relative aux paramètres de processeur

La table suivante fournit des suggestions pour les paramètres de l’UC :

| Paramètre | Valeur | Informations complémentaires |
|---|---|---|
| Gouverneur de fréquence de l’UC | performances | Consultez la commande **cpupower** |
| ENERGY_PERF_BIAS | performances | Consultez la commande **x86_energy_perf_policy** |
| min_perf_pct | 100 | Consultez votre documentation sur l’état P Intel |
| États C | C1 uniquement | Consultez la documentation Linux ou de votre système pour savoir comment garantir que les états C sont définis sur C1 uniquement |

L’utilisation de **_Tuned_ *_ comme décrit précédemment configure automatiquement les paramètres du gouverneur de fréquence de processeur, ENERGY_PERF_BIAS et min_perf_pct, de manière appropriée, car le profil débit-performance est utilisé comme base pour le profil _* mssql**. Le paramètre des états C doit être configuré manuellement conformément à la documentation fournie par Linux ou le distributeur du système.

#### <a name="disk-settings-recommendations"></a>Recommandations relatives aux paramètres de disque

La table suivante fournit des suggestions pour les paramètres du disque :

| Paramètre | Valeur | Informations complémentaires |
|---|---|---|
| disk `readahead` | 4096 | Consultez la commande `blockdev` |
| paramètres sysctl | kernel.sched_min_granularity_ns = 10000000<br/>kernel.sched_wakeup_granularity_ns = 15000000<br/>vm.dirty_ratio = 40<br/>vm.dirty_background_ratio = 10<br/>vm.swappiness = 1 | Consultez la commande **sysctl** |

**Description :**

- **vm.swappiness** : Ce paramètre contrôle le poids relatif octroyé à la permutation de la mémoire du runtime en limitant le noyau à permuter les pages de mémoire du processus SQL Server.

- **vm.dirty_\** _ : Les accès en écriture aux fichiers SQL Server ne sont pas mis en cache pour répondre aux exigences d’intégrité des données. Ces paramètres permettent de bonnes performances d’écriture asynchrone et réduisent l’impact des E/S de stockage des écritures de mise en cache Linux en permettant une mise en cache suffisamment importante pendant la limitation du vidage.

- _*kernel.sched_\**_ : Ces valeurs de paramètre représentent la recommandation actuelle pour la modification de l’algorithme CFS (Completely Fair Scheduling) dans le noyau Linux, afin d’améliorer le débit des appels d’E/S de réseau et de stockage en ce qui concerne la préemption entre processus et la reprise des threads.

L’utilisation du profil _*mssql** **_Tuned_*_ configure les paramètres _*vm.swappiness**, **vm.dirty_\* *_ et _* kernel.sched_\**_. La configuration de disk `readahead` à l’aide de la commande `blockdev` s’effectue appareil par appareil et doit être effectuée manuellement.

#### <a name="kernel-setting-auto-numa-balancing-for-multi-node-numa-systems"></a>Paramètre de noyau d’équilibrage NUMA automatique pour les systèmes NUMA à plusieurs nœuds

Si vous installez SQL Server sur un système _ *NUMA** à plusieurs nœuds, le paramètre de noyau **kernel.numa_balancing** suivant est activé par défaut. Pour permettre à SQL Server de fonctionner avec un niveau d'efficacité maximal sur un système **NUMA**, désactivez l’équilibrage NUMA automatique sur un système NUMA à plusieurs nœuds :

```bash
sysctl -w kernel.numa_balancing=0
```

L’utilisation du profil **mssql** **_Tuned_ *_ configure l’option _* kernel.numa_balancing**.

#### <a name="kernel-settings-for-virtual-address-space"></a>Paramètres de noyau pour l’espace d’adressage virtuel

La valeur par défaut de **vm. max _map_count** (65536) peut ne pas être suffisamment élevée pour une installation SQL Server. Par conséquent, remplacez la valeur de **vm.max_map_count** par au moins 262144 pour un déploiement SQL Server et reportez-vous à la section [Paramètres Linux proposés avec un profil mssql Tuned](#proposed-linux-settings-using-a-tuned-mssql-profile) pour affiner encore ces paramètres de noyau. La valeur maximale pour vm.max_map_count est 2147483647.

```bash
sysctl -w vm.max_map_count=1600000
```

L’utilisation du profil **mssql** **_Tuned_ *_ configure l’option _* vm.max_map_count**.

#### <a name="leave-transparent-huge-pages-thp-enabled"></a>Laissez les pages volumineuses transparentes (THP) activées

Cette option doit être activée par défaut pour la plupart des installations Linux. Nous vous recommandons d’utiliser les performances les plus cohérentes pour garder cette option de configuration activée. Toutefois, en cas d’activité de pagination sollicitant une grande quantité de mémoire (par exemple, dans le cadre de déploiements SQL Server avec plusieurs instances ou d’une exécution de SQL Server avec d’autres applications nécessitant une grande quantité de mémoire sur le serveur), nous vous suggérons de tester les performances de vos applications après l’exécution de la commande suivante :

```bash
echo madvise > /sys/kernel/mm/transparent_hugepage/enabled
```

Ou modifiez le profil **mssql** **_Tuned_* _ avec la ligne :

```bash
vm.transparent_hugepages=madvise
```

Et activez le profil _ *mssql** après la modification :

```bash
tuned-adm off
tuned-adm profile mssql
```

L’utilisation du profil **mssql** **_Tuned_ *_ configure l’option _* transparent_hugepage**.

#### <a name="additional-advanced-kernelos-configuration"></a>Configuration avancée supplémentaire du noyau/système d’exploitation

1. Pour des performances optimales d’E/S de stockage, il est recommandé d’utiliser la planification Linux à plusieurs files d’attente pour les appareils de traitement par blocs. Cela permet de mettre à l’échelle correctement les performances de la couche de traitement par blocs avec des disques SSD (Solid-State Drive) et des systèmes multicœurs rapides. Consultez la documentation si elle est activée par défaut dans vos distributions Linux. Dans la plupart des autres cas, l’amorçage du noyau avec **scsi_mod.use_blk_mq=y** l’active, même si la documentation de la distribution Linux utilisée peut fournir des instructions supplémentaires à ce sujet. Celle-ci est cohérente avec le noyau Linux en amont.

1. Comme MPIO (Multipath I/O) est souvent utilisé pour les déploiements SQL Server, la cible multivoie du mappeur d’appareil (DM) doit également être configurée pour utiliser l’infrastructure `blk-mq` en activant l’option d’amorçage du noyau **dm_mod.use_blk_mq=y**. La valeur par défaut est `n` (désactivé). Ce paramètre, lorsque les appareils SCSI sous-jacents utilisent `blk-mq`, réduit la surcharge de verrouillage au niveau de la couche DM. Reportez-vous à la documentation de la distribution Linux utilisée pour obtenir des conseils supplémentaires sur la façon de le configurer.

#### <a name="configure-swapfile"></a>Configurer un fichier d’échange

Vérifiez que vous disposez d’un fichier d’échange correctement configuré pour éviter les problèmes de mémoire insuffisante. Consultez la documentation Linux pour savoir comment créer et dimensionner correctement un fichier d’échange.

#### <a name="virtual-machines-and-dynamic-memory"></a>Machines virtuelles et mémoire dynamique

Si vous exécutez SQL Server sur Linux sur une machine virtuelle, assurez-vous de sélectionner des options pour corriger la quantité de mémoire réservée pour la machine virtuelle. N’utilisez pas de fonctionnalités comme Mémoire dynamique Hyper-V.

## <a name="sql-server-configuration"></a>Configuration de SQL Server

Il est recommandé d’effectuer les tâches de configuration suivantes après avoir installé SQL Server sur Linux pour obtenir les meilleures performances pour votre application.

### <a name="best-practices"></a>Meilleures pratiques

- **Utiliser PROCESS AFFINITY pour le nœud et/ou les UC**

   Il est recommandé d’utiliser `ALTER SERVER CONFIGURATION` pour définir `PROCESS AFFINITY` pour tous les nœuds **NUMANODE** et/ou les processeurs que vous utilisez pour SQL Server (généralement pour tous les nœuds et tous les processeurs) sur un système d’exploitation Linux. L’affinité du processus permet de conserver un comportement de planification Linux et SQL efficace. L’utilisation de l’option **NUMANODE** est la méthode la plus simple. Utilisez **PROCESS AFFINITY** même si vous n’avez qu’un seul nœud NUMA sur votre ordinateur. Pour plus d’informations sur la manière de définir **PROCESS AFFINITY**, consultez l’article [ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md).

- **Configurer plusieurs fichiers de données tempdb**

   Étant donné qu’une installation SQL Server sur Linux ne propose pas d’option de configuration de plusieurs fichiers tempdb, nous vous recommandons de considérer la création de plusieurs fichiers de données tempdb après l’installation. Pour plus d’informations, reportez-vous aux instructions de l’article [Suggestions pour réduire la contention d’allocation dans la base de données tempdb SQL Server](https://support.microsoft.com/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d).

### <a name="advanced-configuration"></a>Configuration avancée

Les suggestions suivantes sont des paramètres de configuration facultatifs que vous pouvez choisir d’effectuer après l’installation de SQL Server sur Linux. Ces choix sont basés sur les exigences de votre charge de travail et la configuration de votre système d’exploitation Linux.

- **Définir une limite de mémoire avec mssql-conf**

   Pour garantir qu’il y a suffisamment de mémoire physique disponible pour le système d’exploitation Linux, le processus SQL Server utilise uniquement 80 % de la mémoire RAM physique par défaut. Pour certains systèmes qui ont une grande quantité de mémoire RAM physique, 20 % peut être un nombre significatif. Par exemple, sur un système avec 1 To de RAM, le paramètre par défaut laisse environ 200 Go de RAM inutilisée. Dans ce cas, vous souhaiterez peut-être configurer la limite de la mémoire sur une valeur plus élevée. Consultez la documentation sur l'outil **mssql-conf** et le paramètre [memory.memorylimitmb](sql-server-linux-configure-mssql-conf.md#memorylimit) qui contrôle la mémoire visible pour SQL Server (en mégaoctets).

   Lorsque vous modifiez ce paramètre, veillez à ne pas définir cette valeur trop élevée. Si vous ne laissez pas assez de mémoire, vous pouvez rencontrer des problèmes avec le système d’exploitation Linux et d’autres applications Linux.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les fonctionnalités de SQL Server qui améliorent les performances, consultez [Prise en main des fonctionnalités de performances](sql-server-linux-performance-get-started.md).

Pour plus d’informations sur SQL Server sur Linux, consultez [Vue d’ensemble de SQL Server sur Linux](sql-server-linux-overview.md).
