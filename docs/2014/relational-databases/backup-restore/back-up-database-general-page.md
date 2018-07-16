---
title: Sauvegarder la base de données (page Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.general.f1
ms.assetid: 5c344dfd-1ad3-41cc-98cd-732973b4a162
caps.latest.revision: 59
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 025d5eac30815b6d9110dcca7214e7e88412a23d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290955"
---
# <a name="back-up-database-general-page"></a>Sauvegarder la base de données (page Général)
  La page **Général** de la boîte de dialogue **Sauvegarder la base de données** vous permet d'afficher ou de modifier les paramètres d'une opération de sauvegarde de base de données.  
  
 Pour plus d’informations sur les concepts de base de la sauvegarde, consultez [Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](backup-overview-sql-server.md).  
  
> [!NOTE]  
>  Quand vous spécifiez une tâche de sauvegarde à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous pouvez générer le script [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) correspondant en cliquant sur le bouton **Script** et en sélectionnant une destination pour le script.  
  
 **Pour créer une sauvegarde à l'aide de SQL Server Management Studio**  
  
-   [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Créer une sauvegarde différentielle de base de données &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
    > [!IMPORTANT]  
    >  Vous pouvez définir un plan de maintenance de base de données pour créer des sauvegardes de base de données. Pour plus d'informations, consultez [Plans de maintenance de base de données](http://msdn.microsoft.com/library/ms187658.aspx) dans la documentation en ligne de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] .  
  
 **Pour créer une sauvegarde partielle**  
  
-   Pour créer une sauvegarde partielle, vous devez utiliser l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) avec l'option PARTIAL.  
  
## <a name="options"></a>Options  
  
### <a name="source"></a>Source  
 Les options du volet **Source** identifient la base de données et spécifient le type de sauvegarde et le composant pour l'opération de sauvegarde.  
  
 **Sauvegarde de la base de données**  
 Sélectionnez la base de données à sauvegarder.  
  
 **Mode de récupération**  
 Spécifie le mode de récupération (simple, complète ou avec journal des transactions) pour la base de données sélectionnée.  
  
 **Type de sauvegarde**  
 Sélectionnez le type de sauvegarde que vous voulez réaliser sur la base de données spécifiée.  
  
|Type de sauvegarde|Disponible pour|Restrictions|  
|-----------------|-------------------|------------------|  
|Complète|Bases de données, fichiers et groupes de fichiers|Sur la base de données **master** , seules des sauvegardes complètes sont possibles.<br /><br /> En mode de récupération simple, les sauvegardes des fichiers et des groupes de fichiers sont disponibles uniquement pour les groupes de fichiers en lecture seule.|  
|Différentielle|Bases de données, fichiers et groupes de fichiers|En mode de récupération simple, les sauvegardes des fichiers et des groupes de fichiers sont disponibles uniquement pour les groupes de fichiers en lecture seule.|  
|Journal des transactions|Journaux des transactions|Les sauvegardes des journaux des transactions ne sont pas disponibles en mode de récupération simple.|  
  
 **Sauvegarde de copie uniquement**  
 Permet de créer une sauvegarde de type copie uniquement. Une *sauvegarde de copie uniquement* est une sauvegarde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indépendante du mécanisme des sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conventionnelles. Pour plus d’informations, consultez [Sauvegardes de copie uniquement &#40;SQL Server&#41;](copy-only-backups-sql-server.md).  
  
> [!NOTE]  
>  Lorsque l'option **Différentielle** est sélectionnée, vous ne pouvez pas créer de sauvegarde de copie uniquement.  
  
 **Composant de sauvegarde**  
 Sélectionnez le composant de base de données à sauvegarder. Si **Journal des transactions** est sélectionné dans la liste **Type de sauvegarde** , cette option n'est pas activée.  
  
 Sélectionnez l'une des cases d'option suivantes :  
  
|||  
|-|-|  
|**Sauvegarde de la base de données**|Indique que l'intégralité de la base de données doit être sauvegardée.|  
|**Fichiers et groupes de fichiers**|Indique que les fichiers et/ou groupes de fichiers spécifiés doivent être sauvegardés.<br /><br /> La sélection de cette option provoque l'affichage de la boîte de dialogue **Sélection de fichiers et de groupes de fichiers** . Une fois que vous avez sélectionné les fichiers ou groupes de fichiers à sauvegarder et cliqué sur **OK**, vos sélections apparaissent dans la zone **Fichiers et groupes de fichiers** .|  
  
### <a name="destination"></a>Destination  
 Les options du volet **Destination** vous permettent de spécifier le type d'unité de sauvegarde pour l'opération de sauvegarde et de rechercher une unité de sauvegarde logique ou physique.  
  
> [!NOTE]  
>  Pour plus d’informations sur les unités de sauvegarde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md).  
  
 **Sauvegarde sur**  
 Sélectionnez un des types de support ci-dessous pour la sauvegarde. Les destinations que vous sélectionnez apparaissent dans la liste **Sauvegarde sur** .  
  
|||  
|-|-|  
|**Disque**|Permet de sauvegarder sur un disque. Il peut s'agir d'un fichier système ou d'une unité logique de sauvegarde sur disque créée pour la base de données. Les disques sélectionnés apparaissent dans la liste **Sauvegarde sur** . Vous pouvez sélectionner jusqu'à 64 disques pour l'opération de sauvegarde.|  
|**Bande**|Permet de sauvegarder sur bande. Il peut s'agir d'un lecteur de bandes local ou d'une unité logique de sauvegarde sur bande créée pour la base de données. Les bandes sélectionnées apparaissent dans la liste **Sauvegarde sur** . Le nombre maximal est de 64. Si aucun lecteur de bandes n'est connecté au serveur, cette option est désactivée. Les bandes que vous sélectionnez sont répertoriées dans la liste **Sauvegarde sur** .<br /><br /> Remarque : la prise en charge des unités de sauvegarde sur bande sera supprimée dans une prochaine version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité.|  
|**URL**|Permet de sauvegarder dans le stockage d'objets blob Windows Azure.|  
  
 L'affichage des options suivantes dépend du type de destination sélectionné. Si vous sélectionnez Disque ou Bande, les options suivantes s'affichent.  
  
 **Ajouter**  
 Permet d’ajouter un fichier ou une unité à la liste **Sauvegarde sur** . Vous pouvez sauvegarder jusqu'à 64 unités simultanément sur un disque local ou distant. Pour spécifier un fichier sur un disque distant, utilisez le nom complet UNC (Universal Naming Convention). Pour plus d’informations, consultez [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md).  
  
 **Supprimer**  
 Permet de supprimer une ou plusieurs unités sélectionnées de la liste **Sauvegarde sur** .  
  
 **Sommaire**  
 Permet d'afficher le contenu du support pour l'unité sélectionnée.  
  
 Si vous sélectionnez URL comme destination de sauvegarde, les options suivantes s'affichent :  
  
 **Nom de fichier**  
 Spécifiez le nom du fichier de sauvegarde.  
  
 **Informations d’identification SQL**  
 Sélectionnez les informations d'identification SQL utilisées pour l'authentification au stockage Windows Azure. Si vous n'avez pas d'informations d'identification SQL, cliquez sur le bouton **Créer** pour créer de nouvelles informations d'identification SQL.  
  
> [!IMPORTANT]  
>  La boîte de dialogue qui s'ouvre lorsque vous cliquez sur **Créer** requiert un certificat de gestion ou le profil de publication de l'abonnement. Si vous n'avez pas accès au certificat de gestion ou au profil de publication, vous pouvez créer des informations d'identification SQL en spécifiant le nom du compte de stockage et les informations de clé d'accès à l'aide de Transact-SQL ou de SQL Server Management Studio. Consultez l’exemple de code dans le dans le [pour créer des informations d’identification](../security/authentication-access/create-a-credential.md#Credential) rubrique pour créer des informations d’identification à l’aide de Transact-SQL. Vous pouvez également utiliser SQL Server Management Studio, depuis l'instance du moteur de base de données, et cliquer avec le bouton droit sur **Sécurité**, puis sélectionner **Nouveau**, puis **Informations d'identification**. Spécifiez le nom du compte de stockage pour **Identité** et la clé d'accès dans le champ **Mot de passe** .  
  
 **Conteneur de stockage Windows Azure**  
 Spécifiez le nom du conteneur de stockage Windows Azure.  
  
 **Préfixe d'URL**  
 Est généré automatiquement à partir des informations du compte de stockage contenues dans les informations d'identification SQL, et du nom du conteneur de stockage Windows Azure que vous avez spécifié. Nous vous recommandons de ne pas modifier les informations de ce champ, sauf si vous utilisez un domaine qui utilise un format autre que **\<compte_de_stockage>.blob.core.windows.net**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarder un journal des transactions &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)   
 [Sauvegarder des fichiers et des groupes de fichiers &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)   
 [Définir une unité de sauvegarde logique pour un fichier de disque &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [Définir une unité de sauvegarde logique pour un lecteur de bande &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [Modes de récupération &#40;SQL Server&#41;](recovery-models-sql-server.md)  
  
  
