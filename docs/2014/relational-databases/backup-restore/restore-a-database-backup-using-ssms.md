---
title: Restaurer une sauvegarde de base de données (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.locatebackupfileazure.f1
- sql12.swb.specifybackup.f1
helpviewer_keywords:
- full backups [SQL Server]
- database restores [SQL Server], full backups
- backing up databases [SQL Server], full backups
- database backups [SQL Server], full backups
- restoring databases [SQL Server], full backups
ms.assetid: 24b3311d-5ce0-4581-9a05-5c7c726c7b21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 521fc35b8ada4b1eb6c62e75fed4e1d9f99d21c4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70154777"
---
# <a name="restore-a-database-backup-sql-server-management-studio"></a>Restaurer une sauvegarde de base de données (SQL Server Management Studio)
  Cette rubrique explique comment restaurer une sauvegarde complète de base de données.  
  
> [!IMPORTANT]  
>  Que vous soyez en mode de restauration complète ou en mode de récupération utilisant les journaux de transactions, pour pouvoir restaurer une base de données dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous devez d'abord sauvegarder le journal des transactions actif (appelé fin du journal). Pour plus d’informations, consultez [Sauvegarder un journal des transactions &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md). Pour restaurer une base de données chiffrée, vous devez avoir accès au certificat ou à la clé asymétrique qui a servi à chiffrer la base de données. Sans le certificat et la clé asymétrique, la base de données ne peut pas être restaurée. En conséquence, le certificat utilisé pour chiffrer la clé de chiffrement de base de données doit être conservé tant que la sauvegarde est utile. Pour plus d'informations, consultez [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).  
  
 Notez que si vous restaurez une base de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou d'une version ultérieure vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], la base de données est automatiquement mise à niveau. En général, la base de données est immédiatement disponible. Toutefois si une base de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] comprend des index de recherche en texte intégral, la mise à niveau les importe, les réinitialise ou les reconstruit, en fonction du paramètre de la propriété de serveur **Option de mise à niveau du catalogue de texte intégral** . Si l’option de mise à niveau est définie sur **Importer** ou **Reconstruire**, les index de recherche en texte intégral ne seront pas disponibles pendant la mise à niveau. Selon le volume de données indexé, l'importation peut prendre plusieurs heures et la reconstruction jusqu'à dix fois plus longtemps. Notez aussi que lorsque l’option de mise à niveau est définie sur **Importer**, si aucun catalogue de texte intégral n’est disponible, les index de recherche en texte intégral associés sont reconstruits. Pour plus d’informations sur l’affichage ou la modification du paramètre de la propriété **Option de mise à niveau des index de recherche en texte intégral** , consultez [Gérer et surveiller la recherche en texte intégral pour une instance de serveur](../search/manage-and-monitor-full-text-search-for-a-server-instance.md).  
  
### <a name="to-restore-a-full-database-backup"></a>Pour restaurer une sauvegarde complète de base de données  
  
1.  Après vous être connecté à l’instance appropriée du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dans l’Explorateur d’objets, cliquez sur le nom du serveur pour développer l’arborescence du serveur.  
  
2.  Développez **Bases de données**. Selon la base de données, sélectionnez une base de données utilisateur ou développez **Bases de données système**et sélectionnez une base de données système.  
  
3.  Cliquez avec le bouton droit sur la base de données, pointez sur **tâches**, pointez sur **restaurer**, puis cliquez sur **base de données**pour ouvrir la boîte de dialogue **restaurer la base de données** .  
  
4.  Dans la page **Général** , utilisez la section **Source** pour préciser la source et l'emplacement des jeux de sauvegarde à restaurer. Sélectionnez l’une des options suivantes :  
  
    -   **Sauvegarde de la base de données**  
  
         Sélectionnez la base de données à restaurer dans la liste déroulante. La liste contient uniquement les bases de données qui ont été sauvegardées selon l'historique de sauvegarde **msdb** .  
  
    > [!NOTE]  
    >  Si la sauvegarde est prise à partir d'un serveur différent, le serveur de destination ne disposera pas des informations d'historique de sauvegarde pour la base de données spécifiée. Dans ce cas, sélectionnez **Unité** pour spécifier manuellement le fichier ou l'unité à restaurer.  
  
    -   **Passerelle**  
  
         Cliquez sur le bouton Parcourir (**...**) pour ouvrir la boîte de dialogue **Sélectionner les unités de sauvegarde** . Dans la zone **Type du média de sauvegarde**, sélectionnez l'un des types d'unités proposés. Pour sélectionner une ou plusieurs unités pour la zone **Support de sauvegarde**, cliquez sur **Ajouter**.  
  
         Après avoir ajouté les unités souhaitées à la zone de liste **Support de sauvegarde**, cliquez sur **OK** pour revenir à la page **Général**.  
  
         Dans la zone de liste **Source : Unité : Base de données** , sélectionnez le nom de la base de données à restaurer.  
  
        > [!NOTE]  
        >  Cette liste n’est disponible que quand **Unité** est sélectionné. Seules les bases de données qui ont des copies de sauvegarde sur l'unité sélectionnée seront disponibles.  
  
         **Support de sauvegarde**  
         Sélectionnez le support pour l'opération de restauration : **Fichier**, **Bande**, **URL** ou **Unité de sauvegarde**. L'option **Bande** s'affiche uniquement si un lecteur de bande est connecté à l'ordinateur et l'option **Unité de sauvegarde**, seulement si au moins une unité de sauvegarde est connectée.  
  
         **Emplacement de sauvegarde**  
         Permet d'afficher, d'ajouter ou de supprimer des supports pour l'opération de restauration. La liste peut contenir jusqu'à 64 fichiers, bandes ou unités de sauvegarde.  
  
         **Ajouter**  
         Permet d'ajouter l'emplacement d'une unité de sauvegarde dans la liste **Emplacement de sauvegarde**. Selon le type de support sélectionné dans le champ **Support de sauvegarde**, lorsque vous cliquez sur **Ajouter** une des boîtes de dialogue suivantes s'ouvre.  
  
        |Type de support|Boîte de dialogue|Description|  
        |----------------|----------------|-----------------|  
        |**File**|**Localiser le fichier de sauvegarde**|Dans cette boîte de dialogue, vous pouvez sélectionner un fichier local depuis l'arborescence ou un fichier distant en utilisant son nom complet UNC (Universal Naming Convention). Pour plus d’informations, consultez [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md).|  
        |**Appareil**|**Sélectionner l’unité de sauvegarde**|Dans cette boîte de dialogue, vous pouvez effectuer une sélection à partir d'une liste d'unités logiques de sauvegarde définies sur l'instance de serveur.|  
        |**Bande**|**Sélectionner la bande de sauvegarde**|Dans cette boîte de dialogue, vous pouvez effectuer une sélection à partir d'une liste de lecteurs de bande physiquement connectés à l'ordinateur exécutant l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
        |**URL**|Deux boîtes de dialogue sont lancées dans l'ordre suivant :<br /><br /> 1) **Connectez-vous à Azure Storage**<br /><br /> 2) **localiser le fichier de sauvegarde dans Azure**|Dans la boîte de dialogue **connexion au stockage Azure** , sélectionnez les informations d’identification SQL existantes qui stockent le nom du compte de stockage Azure et les informations de clé d’accès, ou créez de nouvelles informations d’identification SQL en spécifiant le nom du compte de stockage et les informations sur la clé d’accès de stockage. Pour plus d’informations, consultez [se connecter au stockage Azure &#40;&#41;de restauration ](connect-to-microsoft-azure-storage-restore.md).<br /><br /> Dans la boîte de dialogue **Localiser le fichier de sauvegarde**, vous pouvez sélectionner un fichier dans la liste de conteneurs affichée dans le volet gauche.|  
  
         Si la liste est pleine, le bouton **Ajouter** n’est pas disponible.  
  
         **Remove**  
         Supprime un ou plusieurs fichiers, bandes ou unités logiques de sauvegarde sélectionnés.  
  
         **Contents**  
         Affiche le contenu du support d'un fichier, d'une bande ou d'une unité logique de sauvegarde sélectionné(e).  
  
5.  Dans la section **Destination** , la zone **Base de données** est automatiquement renseignée avec le nom de la base de données à restaurer. Pour changer le nom de la base de données, entrez le nouveau nom dans la zone **Base de données** .  
  
6.  Dans la zone **Restaurer sur**, laissez la valeur par défaut **Vers la dernière sauvegarde prise** ou cliquez sur **Chronologie** pour accéder à la boîte de dialogue **Chronologie de sauvegarde** afin de sélectionner manuellement une limite spécifique pour arrêter l'action de récupération. Pour plus d’informations sur la façon de désigner une limite spécifique, consultez [Chronologie de sauvegarde](backup-timeline.md).  
  
7.  Dans la grille **Jeux de sauvegarde à restaurer**, sélectionnez les sauvegardes à restaurer. Cette grille affiche les sauvegardes disponibles pour l'emplacement spécifié. Par défaut, un plan de récupération est suggéré. Pour ignorer le plan de récupération suggéré, vous pouvez modifier les sélections dans la grille. Les sauvegardes qui dépendent de la restauration d'une sauvegarde antérieure sont automatiquement désélectionnées dès lors que la sauvegarde antérieure est désélectionnée. Pour plus d’informations sur les colonnes de la grille **Jeux de sauvegarde à restaurer** , consultez [Restaurer la base de données &#40;page Général&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).  
  
8.  Vous pouvez aussi cliquer sur **Fichiers** dans le volet **Sélectionner une page** pour accéder à la boîte de dialogue **Fichiers** . Vous pouvez alors restaurer la base de données vers un nouvel emplacement, en spécifiant une nouvelle destination de restauration pour chaque fichier dans la grille **Restaurer les fichiers de la base de données en tant que**. Pour plus d’informations sur cette grille, consultez [Restaurer la base de données &#40;page Fichiers&#41;](restore-database-files-page.md).  
  
9. Pour afficher ou sélectionner les options avancées, dans la page **Options**, dans le volet **Options de restauration**, vous pouvez choisir les options suivantes si elles s’appliquent à votre situation :  
  
    1.  Options `WITH` (non obligatoires) :  
  
        -   **REMPLACER la base de données existante (WITH REPLACE)**  
  
        -   **Conserver les paramètres de réplication (avec KEEP_REPLICATION)**  
  
        -   **Restreindre l’accès à la base de données restaurée (avec RESTRICTED_USER)**  
  
    2.  Sélectionnez une option pour la zone **État de récupération** . Cette zone détermine l'état de la base de données à l'issue de l'opération de restauration.  
  
        -   **Restore with Recovery** est le comportement par défaut qui laisse la base de données opérationnelle en restaurant les transactions non validées. Les journaux des transactions supplémentaires ne peuvent pas être restaurés. Choisissez cette option si vous restaurez toutes les sauvegardes nécessaires maintenant.  
  
        -   **RESTORE WITH NORECOVERY** qui laisse la base de données non opérationnelle et ne restaure pas les transactions non validées. Les journaux des transactions supplémentaires peuvent être restaurés. La base de données ne peut pas être utilisée tant qu'elle n'est pas récupérée.  
  
        -   **Restore with Standby** qui laisse la base de données en mode lecture seule. Elle annule les transactions non validées, mais enregistre les actions d'annulation dans un fichier afin de rendre réversibles les effets de la récupération.  
  
    3.  **Effectuer une sauvegarde de la fin du journal avant la restauration** est sélectionnée si elle est nécessaire pour le moment que vous avez sélectionné. Vous n'avez pas besoin de modifier ce paramètre, mais vous pouvez choisir de sauvegarder la fin du journal même si ce n'est pas obligatoire. fichier ici ? Si le premier jeu de sauvegarde de la page **général** est dans Azure, le journal de la fin est également sauvegardé dans le même conteneur de stockage.  
  
    4.  Les opérations de restauration peuvent échouer s'il existe des connexions actives à la base de données. Activez l'option **Fermer les connexions existantes** pour garantir que toutes les connexions actives entre [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] et la base de données sont fermées. Cette case à cocher définit la base de données en mode mono-utilisateur avant d'effectuer les opérations de restauration, et définit la base de données en mode multi-utilisateur une fois l'opération terminée.  
  
    5.  Sélectionnez **Demander confirmation avant chaque restauration de sauvegarde** si vous souhaitez être invité entre chaque opération de restauration. Cela n'est généralement pas nécessaire à moins que la base de données ne soit volumineuse et que vous ne souhaitiez surveiller l'état de l'opération de restauration.  
  
     Pour plus d’informations sur ces options de restauration, consultez [Restaurer la base de données &#40;page Options&#41;](restore-database-options-page.md).  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarder un journal des transactions &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)   
 [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)   
 [Restaurer une base de données à un nouvel emplacement &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md)   
 [Restaurer une sauvegarde de journal des transactions &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Restaurer la base de données &#40;page Options&#41;](restore-database-options-page.md)   
 [Restaurer la base de données &#40;page Général&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
  
