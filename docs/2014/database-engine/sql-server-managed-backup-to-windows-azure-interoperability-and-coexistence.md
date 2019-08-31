---
title: 'SQL Server la gestion de sauvegarde sur Azure: Interopérabilité et coexistence | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 78fb78ed-653f-45fe-a02a-a66519bfee1b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 70d941786fd06e48bf071b8448b84c8f4857f8c8
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176067"
---
# <a name="sql-server-managed-backup-to-azure-interoperability-and-coexistence"></a>SQL Server la gestion de sauvegarde sur Azure: Interopérabilité et coexistence
  Cette rubrique présente l'interopérabilité et la coexistence de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] avec plusieurs fonctionnalités dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Ces fonctionnalités incluent les suivantes : Groupes de disponibilité AlwaysOn, mise en miroir de bases de données, plans de maintenance de sauvegarde, envoi de journaux, sauvegardes ad hoc, détacher la base de données et supprimer la base de données.  
  
### <a name="alwayson-availability-groups"></a>Groupes de disponibilité AlwaysOn  
 Groupes de disponibilité AlwaysOn configurés en tant que solution Azure uniquement prise en charge [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]pour. Les configurations de groupes de disponibilité AlwaysOn locaux ou hybrides ne sont pas prises en charge. Pour plus d’informations et d’autres éléments à prendre en considération, consultez [configuration d’SQL Server gestion de la sauvegarde sur Azure pour les groupes de disponibilité](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)  
  
### <a name="database-mirroring"></a>Mise en miroir de bases de données  
 La [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est prise en charge uniquement sur la base de données principale. Si la base de données principale et le miroir sont configurés pour utiliser la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], la base de données mise en miroir est ignorée et ne sera pas sauvegardée. Toutefois, en cas de basculement, la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] commence le processus de sauvegarde après que le miroir a terminé de permuter le rôle, et est en ligne. Dans ce cas, les sauvegardes seront restaurées dans un nouveau conteneur. Si le miroir n'est pas configuré pour utiliser la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], en cas de basculement, aucune sauvegarde n'est effectuée. Nous vous recommandons de configurer la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] sur le serveur principal et le miroir de façon à ce que les sauvegardes continuent en cas de basculement.  
  
> [!TIP]  
>  Si vous créez une base de données mise en miroir sur une instance avec les paramètres par défaut de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], il peut être préférable de désactiver les valeurs par défaut de d'instance [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], de façon à ce qu'elles ne soient pas appliquées à la base de données mise en miroir, puis de les réactiver après avoir configuré le principal et le miroir.  
  
### <a name="maintenance-plan"></a>Plan de maintenance  
 L'utilisation de plans de maintenance pour créer des sauvegardes d'une base de données lorsque la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est activée n'est pas prise en charge. Les plans de maintenance vont rompre la séquence de journaux de transactions consécutifs et la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] peut ne pas être en mesure d'assurer la récupérabilité de la base de données lors de la restauration. Cela s'applique également si la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est activée au niveau de l'instance.  
  
> [!TIP]  
>  Les plans de maintenance avec des sauvegardes de type copie seule sont pris en charge par la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configurée pour la même base de données ou instance.  
  
### <a name="log-shipping"></a>Copie des journaux de transactions  
 Vous ne pouvez pas configurer la copie des journaux de transactions et la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] simultanément pour la même base de données. Cela affecte la récupérabilité de la base de données de l'une ou l'autre fonctionnalité.  
  
### <a name="ad-hoc-backups-using-transact-sql-and-sql-server-management-studio"></a>Sauvegardes ad hoc à l'aide de Transact-SQL et SQL Server Management Studio  
 Les sauvegardes ad hoc ou uniques créées hors de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] avec Transact-SQL ou SQL Server Management Studio peuvent affecter le processus de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] en fonction du type de sauvegarde et du support de stockage utilisé. Les sauvegardes de journaux vers un autre compte de stockage [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Azure que celui qui utilise, ou toute autre destination que le service de stockage d’objets BLOB Azure, entraînent une rupture de la séquence de journaux. Nous vous recommandons d’utiliser la procédure stockée [Transact- &#40;SQL&#41; smart_admin. sp_backup_on_demand](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql) pour lancer une sauvegarde sur les bases de [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] données qui sont activées. Effectuez une sauvegarde de base de données complète ou bien une sauvegarde de fichier journal en utilisant cette procédure stockée.  
  
### <a name="drop-database-and-detach-database"></a>Supprimer et détacher une base de données  
 Si une base de données activée pour la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] est supprimée ou détachée, bien qu'aucune sauvegarde ne soit plus possible, les sauvegardes précédentes restent dans le stockage jusqu'à l'expiration de la période de rétention, après quoi, elles seront purgées.  
  
### <a name="changes-to-recovery-model"></a>Changements apportés au modèle de récupération  
  
-   Si vous modifiez le mode de récupération d’une base de données de **simple** à **complet** ou **journalisé en bloc**, vous avez [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] la possibilité de configurer pour la base de données. La base de données sera considérée comme une nouvelle base de données par la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].  
  
-   Si vous modifiez le mode de récupération d’une base de données **complète** ou de la **journalisation en bloc** en **simple**, qui est [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] activée, les opérations de sauvegarde ne seront plus planifiées. Le paramètre de période de rétention continue d'être appliqué et les fichiers de sauvegarde resteront dans le compte de stockage jusqu'à l'expiration de la période de rétention. Si vous souhaitez conserver les sauvegardes, nous vous recommandons de télécharger les fichiers dans un compte de stockage différent ou dans un emplacement local. Les paramètres de configuration sont conservés et peuvent être réutilisés si le mode de récupération est de nouveau défini sur **complet** ou **journalisé en bloc** .  
  
### <a name="log-backups-using-other-backup-tools-or-custom-scripts"></a>Sauvegarde de fichier journal avec d'autres outils de sauvegarde ou des scripts personnalisés  
 Deux sauvegardes qui sont configurées pour effectuer des sauvegardes de fichier journal sur la même base de données entraîneront une interruption de la séquence des journaux de sauvegarde. Bien que la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] tente de remédier à l'interruption dans la séquence de sauvegarde en planifiant des sauvegardes complètes lorsqu'une interruption est détectée, cela revient à suivre de façon permanente les interruptions périodiques et les sauvegardes de fichier journal effectuées par deux outils concurrents. Cela peut également affecter la récupérabilité de la base de données car aucun outil ne peut avoir un jeu complet de sauvegardes en séquence. Bien que cela s'applique à toutes les fonctionnalités ou outils effectuant des sauvegardes de fichier journal, il est utile de donner des exemples spécifiques, comme décrit ci-dessous. Cela sert également à résoudre les problèmes de configuration des plans de maintenance ou de copie des journaux de transaction décrits dans les premières sections de cette rubrique.  
  
 **Sauvegardes basées sur Data Protection Manager (DPM):** Microsoft Data Protection Manager vous permet d’effectuer des sauvegardes complètes et incrémentielles. Les sauvegardes incrémentielles sont des sauvegardes de fichier journal qui effectuent une troncation de journal après la création d'une sauvegarde de fichier journal T. Par conséquent, la configuration de DPM et de la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] pour la même base de données n'est pas prise en charge.  
  
 **Outils tiers ou scripts:** Les outils tiers ou les scripts qui effectuent des sauvegardes de journaux provoquant la troncation [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]du journal ne sont pas compatibles avec et ne sont pas pris en charge.  
  
 Si vous avez [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] activé la pour une instance de base de données et que vous souhaitez effectuer une sauvegarde ad hoc, vous pouvez utiliser la procédure stockée [Transact-SQL &#40;&#41; smart_admin. sp_backup_on_demand](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql) , comme décrit dans la section précédente. Si vous avez également besoin de planifier des sauvegardes régulièrement en dehors la [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], utilisez la sauvegarde de copie uniquement.  Pour plus d’informations, consultez [Sauvegardes de copie uniquement &#40;SQL Server&#41;](../relational-databases/backup-restore/copy-only-backups-sql-server.md).  
  
  
