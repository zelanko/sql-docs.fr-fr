---
title: Service de stockage d’objets Blob SQL Server Backup and Restore avec Windows Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6a0c9b6a-cf71-4311-82f2-12c445f63935
caps.latest.revision: 28
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 38e20e433b7fed2e34750c300ee7e1489d6df665
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37193549"
---
# <a name="sql-server-backup-and-restore-with-windows-azure-blob-storage-service"></a>Sauvegarde et restauration SQL Server avec le service de Stockage Blob Windows Azure
  Cette rubrique présente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de sauvegardes et de restauration à partir de la [service de stockage d’objets Blob Windows Azure](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/). Elle résume également les avantages liés à l'utilisation du service d'objets blob Windows Azure pour stocker des sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 SQL Server prend en charge le stockage des sauvegardes dans le service de stockage d'objets blob Windows Azure comme suit :  
  
-   **Gérer vos sauvegardes dans Windows Azure :** avec les mêmes méthodes utilisées pour sauvegarde sur disque et sur bande, vous pouvez désormais sauvegarder dans le stockage Windows Azure en spécifiant une URL comme destination de sauvegarde.  Utilisez cette fonctionnalité pour sauvegarder ou configurer manuellement votre propre stratégie de sauvegarde comme vous le feriez pour un stockage local ou d'autres options hors site. Cette fonctionnalité est également connue sous le nom **Sauvegarde SQL Server vers une URL**. Pour plus d'informations, consultez [SQL Server Backup to URL](sql-server-backup-to-url.md). Cette fonctionnalité est disponible dans SQL Server 2012 SP1 CU2 ou version ultérieure.  
  
    > [!NOTE]  
    >  Pour les versions de SQL Server antérieures à SQL Server 2014, utilisez le complément SQL Server Backup to Windows Azure Tool afin de créer rapidement et facilement des sauvegardes dans le Stockage Microsoft Azure. Pour plus d'informations, consultez le [centre de téléchargement](http://go.microsoft.com/fwlink/?LinkID=324399).  
  
-   **Laisser SQL Server gérer les sauvegardes dans Windows Azure :** configurer SQL Server pour gérer les sauvegardes de la stratégie et la planification de sauvegarde pour une base de données unique ou plusieurs bases de données, ou définir des valeurs par défaut au niveau de l’instance. Cette fonctionnalité est appelée **[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]**. Pour plus d’informations, consultez [SQL Server Managed Backup pour Windows Azure](sql-server-managed-backup-to-microsoft-azure.md). Cette fonctionnalité est disponible dans SQL Server 2014 ou version ultérieure.  
  
## <a name="benefits-of-using-the-windows-azure-blob-service-for-includessnoversionincludesssnoversion-mdmd-backups"></a>Avantages de l'utilisation du service d'objets blob Windows Azure pour les sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Stockage hors site flexible, fiable et illimité : le stockage de vos sauvegardes dans le service d'objets blob Windows Azure peut représenter une option hors site pratique, flexible et facile d'accès. La création d'un stockage hors site pour vos sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être aussi simple que la modification de vos scripts/tâches existants. En principe, le stockage hors site doit être suffisamment éloigné de l'emplacement de la base de données de production pour empêcher qu'un éventuel sinistre n'affecte tous les emplacements (bases de données hors site et de production). En choisissant de géorépliquer le stockage d'objets blob, vous disposez d'un niveau de protection supplémentaire au cas où un sinistre affecterait l'ensemble de la région. En outre, les sauvegardes restent accessibles à partir de n'importe quel endroit et à tout moment, et vous pouvez y accéder facilement pour les restaurations.  
  
-   Archive de sauvegarde : le service de Stockage Blob Windows Azure offre une meilleure alternative à l'option de stockage sur bande souvent utilisée pour archiver les sauvegardes. Le stockage sur bande peut nécessiter le transport physique vers un emplacement hors site, ainsi que des mesures de protection des supports. En stockant vos sauvegardes dans le service de stockage d'objets blob Windows Azure, vous disposez d'une option d'archivage instantanée, hautement disponible et durable.  
  
-   Aucune surcharge de gestion du matériel avec les services Windows Azure. Les services Windows Azure gèrent le matériel et assurent la géoréplication pour la redondance et la protection contre les défaillances matérielles.  
  
-   Actuellement, pour les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécutant sur un ordinateur virtuel Windows Azure, la sauvegarde dans les services stockage d'objets blob Windows Azure peut être réalisée en créant des disques attachés. Toutefois, le nombre de disques que vous pouvez attacher à un ordinateur virtuel Windows Azure est limité. Cette limite est de 16 disques pour une instance extra-large et inférieure pour les instances plus petites. En activant une sauvegarde directe dans le stockage d'objets blob Windows Azure, vous pouvez contourner la limite de 16 disques.  
  
     En outre, le fichier de sauvegarde qui est maintenant stocké dans le service de stockage d'objets blob Windows Azure est directement accessible pour une instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécutant sur un ordinateur virtuel Windows Azure, sans avoir besoin d'attacher/détacher la base de données ou de télécharger et attacher le disque dur virtuel.  
  
-   Avantages en termes de coûts : payez uniquement pour le service utilisé. Peut être économique comme option de sauvegarde et d'archivage hors site. Consultez le [considérations sur la facturation Windows Azure](#Billing) pour plus d’informations et des liens.  
  
##  <a name="Billing"></a> Windows Azure considérations sur la facturation :  
 En comprenant les coûts de stockage Windows Azure, vous pouvez prévoir le coût de création et de stockage des sauvegardes dans Windows Azure.  
  
 Le [calculatrice de tarification Windows Azure](http://go.microsoft.com/fwlink/?LinkId=277060) peut aider à estimer les coûts.  
  
 **Stockage :** les tarifs sont basés sur l'espace utilisé et sont calculés sur une échelle graduée en fonction du niveau de redondance. Pour plus d’informations, consultez la section **Gestion des données** de l’article [Détails de la tarification](http://go.microsoft.com/fwlink/?LinkId=277059) .  
  
 **Les transferts de données :** vers Windows Azure, les transferts de données entrantes sont gratuits. Les transferts sortants sont facturés en fonction de l'utilisation de la bande passante et calculés selon une échelle graduée spécifique à la région. Pour plus d'informations, consultez la section [Transferts de données](http://go.microsoft.com/fwlink/?LinkId=277061) de l'article Détails de la tarification.  
  
## <a name="see-also"></a>Voir aussi  
 [Meilleures pratiques et dépannage de sauvegarde SQL Server vers une URL](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [Sauvegarder et restaurer des bases de données système &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [Didacticiel : Sauvegarde de SQL Server et de la restauration au Service de stockage Windows Azure Blob](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)   
 [Sauvegarde SQL Server vers une URL](sql-server-backup-to-url.md)  
  
  
