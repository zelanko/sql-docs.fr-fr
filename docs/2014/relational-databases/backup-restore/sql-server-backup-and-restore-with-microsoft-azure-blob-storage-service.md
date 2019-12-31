---
title: SQL Server la sauvegarde et la restauration avec le service de stockage d’objets BLOB Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 6a0c9b6a-cf71-4311-82f2-12c445f63935
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 38c92e397c971f6e9976bb857c63410fa60b7e85
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75232429"
---
# <a name="sql-server-backup-and-restore-with-azure-blob-storage-service"></a>Sauvegarde et restauration SQL Server avec le service Stockage Blob Azure
  Cette rubrique présente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les sauvegardes et les restaurations à partir du [service de stockage d’objets BLOB Azure](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/). Il fournit également un résumé des avantages de l’utilisation du service BLOB Azure pour stocker [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les sauvegardes.  
  
 SQL Server prend en charge le stockage des sauvegardes dans le service de stockage d’objets BLOB Azure des manières suivantes :  
  
-   **Gérez vos sauvegardes dans Azure :** À l’aide des mêmes méthodes que celles utilisées pour sauvegarder sur disque et sur bande, vous pouvez maintenant effectuer une sauvegarde dans le stockage Azure en spécifiant l’URL comme destination de sauvegarde.  Utilisez cette fonctionnalité pour sauvegarder ou configurer manuellement votre propre stratégie de sauvegarde comme vous le feriez pour un stockage local ou d'autres options hors site. Cette fonctionnalité est également connue sous le nom **Sauvegarde SQL Server vers une URL**. Pour plus d’informations, voir [SQL Server Backup to URL](sql-server-backup-to-url.md)(en anglais). Cette fonctionnalité est disponible dans SQL Server 2012 SP1 CU2 ou version ultérieure.  
  
    > [!NOTE]  
    >  Pour les versions SQL Server antérieures à SQL Server 2014, vous pouvez utiliser le complément SQL Server la sauvegarde dans Azure pour créer rapidement et facilement des sauvegardes dans le stockage Azure. Pour plus d'informations, consultez le [centre de téléchargement](https://go.microsoft.com/fwlink/?LinkID=324399).  
  
-   **Laissez SQL Server gérer les sauvegardes dans Azure :** Configurez SQL Server pour gérer la stratégie de sauvegarde et planifier des sauvegardes pour une ou plusieurs bases de données, ou définissez les valeurs par défaut au niveau de l’instance. Cette fonctionnalité est appelée **[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]**. Pour plus d’informations, consultez [SQL Server Managed Backup to Azure](sql-server-managed-backup-to-microsoft-azure.md). Cette fonctionnalité est disponible dans SQL Server 2014 ou version ultérieure.  
  
## <a name="benefits-of-using-the-azure-blob-service-for-includessnoversionincludesssnoversion-mdmd-backups"></a>Avantages de l’utilisation du service d’objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] BLOB Azure pour les sauvegardes  
  
-   Stockage hors site flexible, fiable et illimité : le stockage de vos sauvegardes sur le service BLOB Azure peut être une option hors site pratique, flexible et facile d’accès. La création d'un stockage hors site pour vos sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être aussi simple que la modification de vos scripts/tâches existants. Le stockage hors site doit généralement être suffisamment éloigné de l'emplacement de la base de données de production afin d'empêcher qu'un seul sinistre touche à la fois l'emplacement hors site et la base de données de production. En choisissant de géorépliquer le stockage d'objets blob, vous disposez d'un niveau de protection supplémentaire au cas où un sinistre affecterait l'ensemble de la région. En outre, les sauvegardes restent accessibles à partir de n'importe quel endroit et à tout moment, et vous pouvez y accéder facilement pour les restaurations.  
  
-   Archive de sauvegarde : le service de stockage d’objets BLOB Azure offre une meilleure alternative à l’option de bande souvent utilisée pour archiver les sauvegardes. Le stockage sur bande peut nécessiter un transport physique vers une installation hors site ainsi que la prise de mesures de protection du support. Le stockage de vos sauvegardes dans le service BLOB Azure offre une option d’archivage instantané, hautement disponible et durable.  
  
-   Aucune surcharge de gestion du matériel : il n’y a aucune surcharge de gestion du matériel avec les services Azure. Ces derniers gèrent le matériel et fournissent une géo-réplication à des fins de redondance et de protection contre les défaillances matérielles.  
  
-   Actuellement, pour les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances de s’exécutant sur une machine virtuelle Azure, la sauvegarde dans les services de stockage BLOB Azure peut être réalisée en créant des disques attachés. Toutefois, le nombre de disques que vous pouvez attacher à une machine virtuelle Azure est limité. Cette limite est de 16 disques pour une instance très volumineuse et un nombre inférieur pour les instances plus petites. En activant une sauvegarde directe dans le stockage d’objets BLOB Azure, vous pouvez contourner la limite de 16 disques.  
  
     En outre, le fichier de sauvegarde qui est maintenant stocké dans le service de stockage d’objets BLOB Azure est directement disponible pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] local ou un autre s’exécutant sur une machine virtuelle Azure, sans qu’il soit nécessaire d’attacher/détacher la base de données ou de télécharger et d’attacher le disque dur virtuel.  
  
-   Avantages en termes de coûts : payez uniquement pour le service utilisé. Peut être économique comme option d'archivage hors site et de sauvegarde. Pour plus d’informations et de liens, consultez la section [Considérations sur la facturation Azure](#Billing) .  
  
##  <a name="Billing"></a>Considérations sur la facturation Azure :  
 La compréhension des coûts de stockage Azure vous permet de prévoir le coût de création et de stockage des sauvegardes dans Azure.  
  
 La [calculatrice de prix Azure](https://go.microsoft.com/fwlink/?LinkId=277060) peut vous aider à estimer vos coûts.  
  
 **Stockage :** Les frais sont basés sur l’espace utilisé et sont calculés sur une échelle graduée et le niveau de redondance. Pour plus d’informations, consultez la section **Gestion des données** de l’article [Détails de la tarification](https://go.microsoft.com/fwlink/?LinkId=277059) .  
  
 **Transferts de données :** Les transferts de données entrants vers Azure sont gratuits. Les transferts sortants sont facturés en fonction de l'utilisation de la bande passante et calculés selon une échelle graduée spécifique à la région. Pour plus d'informations, consultez la section [Transferts de données](https://go.microsoft.com/fwlink/?LinkId=277061) de l'article Détails de la tarification.  
  
## <a name="see-also"></a>Voir aussi  
 [Meilleures pratiques et dépannage de la SQL Server sauvegarde vers une URL](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [Sauvegarde et restauration des bases de données système &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [Didacticiel : SQL Server la sauvegarde et la restauration dans le service de stockage d’objets BLOB Azure](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)   
 [SQL Server la sauvegarde vers l’URL](sql-server-backup-to-url.md)  
  
