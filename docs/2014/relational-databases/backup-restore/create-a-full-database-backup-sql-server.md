---
title: Créer une sauvegarde complète de base de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], full backups
- backing up databases [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- database backups [SQL Server], SQL Server Management Studio
ms.assetid: 586561fc-dfbb-4842-84f8-204a9100a534
caps.latest.revision: 51
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7d5d52c835ea69914d538138cf189c7171e07a78
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320439"
---
# <a name="create-a-full-database-backup-sql-server"></a>Créer une sauvegarde complète de base de données (SQL Server)
  Cette rubrique explique comment créer une sauvegarde de base de données complète dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de PowerShell.  
  
> [!NOTE]  
>  Pour plus d'informations sur la sauvegarde SQL Server dans le service de stockage d'objets blob Windows Azure, consultez [SQL Server Backup and Restore with Windows Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour créer une base de données complète à l’aide de la sauvegarde :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   L'instruction BACKUP n'est pas autorisée dans une transaction explicite ou implicite.  
  
-   Les sauvegardes créées avec une version plus récente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peuvent pas être restaurées dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pour plus d’informations, consultez [Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](backup-overview-sql-server.md).  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   À mesure que la taille d'une base de données augmente, les sauvegardes complètes de base de données nécessitent davantage de temps et d'espace de stockage. Par conséquent, pour les bases de données volumineuses, il est conseillé de compléter les sauvegardes complètes avec une série de *sauvegardes différentielles de base de données*. Pour plus d’informations, consultez [Sauvegardes différentielles &#40;SQL Server&#41;](differential-backups-sql-server.md).  
  
-   Vous pouvez estimer la taille d'une sauvegarde complète de base de données en utilisant la procédure stockée système [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) .  
  
-   Par défaut, chaque opération de sauvegarde réussie ajoute une entrée au journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et au journal des événements système. Si vous sauvegardez très fréquemment le journal, ces messages de réussite peuvent rapidement s'accumuler, créer des journaux d'erreurs très volumineux et compliquer la recherche d'autres messages. Dans de tels cas, vous pouvez supprimer ces entrées de journal en utilisant l'indicateur de trace 3226 si aucun de vos scripts ne dépend de ces entrées. Pour plus d’informations, consultez [Indicateurs de trace &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
###  <a name="Security"></a> Sécurité  
 TRUSTWORTHY a la valeur OFF pour une sauvegarde de base de données. Pour plus d’informations sur la façon d’affecter la valeur ON à TRUSTWORTHY, consultez [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
 À partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] le `PASSWORD` et `MEDIAPASSWORD` options sont suspendues pour la création de sauvegardes. Vous pouvez toujours restaurer les sauvegardes créées avec des mots de passe.  
  
####  <a name="Permissions"></a> Permissions  
 Les autorisations BACKUP DATABASE et BACKUP LOG reviennent par défaut aux membres du rôle serveur fixe **sysadmin** et des rôles de base de données fixes **db_owner** et **db_backupoperator** .  
  
 Des problèmes de propriété et d'autorisations sur le fichier physique de l'unité de sauvegarde sont susceptibles de perturber une opération de sauvegarde. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être en mesure de lire et d'écrire sur l'unité ; le compte sous lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute doit avoir des autorisations d'écriture. Toutefois, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), qui ajoute une entrée pour une unité de sauvegarde dans les tables système, ne vérifie pas les autorisations d’accès au fichier. De tels problèmes pour le fichier physique de l'unité de sauvegarde peuvent n'apparaître que lorsque la ressource physique est sollicitée au moment de la sauvegarde ou de la restauration.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
> [!NOTE]  
>  Si vous spécifiez une tâche de sauvegarde à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous pouvez générer le script [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) correspondant en cliquant sur le bouton **Script** et en sélectionnant une destination de script.  
  
#### <a name="to-back-up-a-database"></a>Pour sauvegarder une base de données  
  
1.  Après la connexion à l'instance appropriée du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dans l'Explorateur d'objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Bases de données**puis, selon la base de données, sélectionnez une base de données utilisateur ou développez **Bases de données système** et sélectionnez une base de données système.  
  
3.  Cliquez avec le bouton droit sur la base de données, pointez sur **Tâches**, puis cliquez sur **Sauvegarder**. La boîte de dialogue **Sauvegarder la base de données** s'affiche.  
  
4.  Dans la `Database` zone de liste, vérifiez le nom de la base de données. Vous pouvez éventuellement sélectionner une autre base de données dans la liste.  
  
5.  Il est possible d'effectuer une sauvegarde de base de données pour tout mode de récupération (**FULL**, **BULK_LOGGED**ou **SIMPLE**).  
  
6.  Dans la zone de liste **Type de sauvegarde** , sélectionnez **Complète**.  
  
     Notez qu’après la création d’une sauvegarde de base de données complète, vous pouvez créer une sauvegarde de base de données différentielle. Pour plus d’informations, consultez [Créer une sauvegarde différentielle de base de données &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md).  
  
7.  Vous pouvez si vous le souhaitez sélectionner **Sauvegarde de copie uniquement** pour créer une sauvegarde de copie uniquement. Une *sauvegarde de copie uniquement* est une sauvegarde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indépendante du mécanisme des sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conventionnelles. Pour plus d’informations, consultez [Sauvegardes de copie uniquement &#40;SQL Server&#41;](copy-only-backups-sql-server.md).  
  
    > [!NOTE]  
    >  Lorsque l'option **Différentielle** est sélectionnée, vous ne pouvez pas créer de sauvegarde de copie uniquement.  
  
8.  Pour **composant de sauvegarde**, cliquez sur `Database`.  
  
9. Acceptez le nom du jeu de sauvegarde par défaut proposé dans la zone de texte **Nom** , ou attribuez-lui un autre nom.  
  
10. Dans la zone de texte **Description** , vous avez la possibilité de saisir une description du jeu de sauvegarde.  
  
11. Choisissez le type de destination de la sauvegarde en cliquant sur **Disque**, **Bande** ou **URL**. Pour sélectionner les chemins d'accès à 64 lecteurs de bande ou de disque au maximum contenant un seul support de sauvegarde, cliquez sur **Ajouter**. Les chemins d'accès sélectionnés apparaissent dans la zone de liste **Sauvegarde sur** .  
  
     Pour supprimer une destination de sauvegarde, sélectionnez-la, puis cliquez sur **Supprimer**. Pour afficher le contenu d'une destination de sauvegarde, sélectionnez-la, puis cliquez sur **Sommaire**.  
  
12. Pour afficher ou sélectionner les options de support, cliquez sur **Options de support** dans le volet **Sélectionner une page** .  
  
13. Sélectionnez une option **Remplacer le support** en cliquant sur un des éléments suivants :  
  
    -   **Sauvegarder sur le support de sauvegarde existant**  
  
         Pour cette option, cliquez sur **Ajouter au jeu de sauvegarde existant** ou sur **Remplacer tous les jeux de sauvegarde existants**. Pour plus d’informations, consultez [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
         Vous pouvez aussi activer la case à cocher **Vérifier le nom du support de sauvegarde et la date d'expiration du jeu de sauvegarde** pour forcer l'opération de sauvegarde à vérifier la date et l'heure de l'expiration du jeu de supports ou du jeu de sauvegarde.  
  
         Vous pouvez éventuellement entrer un nom dans la zone de texte **Nom du support de sauvegarde** . Si aucun nom n'est spécifié, un support de sauvegarde avec un nom vide est créé. Si vous spécifiez un nom pour le support de sauvegarde, ce support (bande ou disque) est vérifié pour voir si le nom réel correspond bien au nom que vous entrez ici.  
  
        > [!IMPORTANT]  
        >  Cette option est désactivée si vous avez sélectionné **URL** comme destination de la sauvegarde dans la page **Général** . Pour plus d’informations, consultez [Sauvegarder la base de données &#40;page Options de support&#41;](back-up-database-media-options-page.md)  
        >   
        >  Si vous envisagez d'utiliser le chiffrement, ne sélectionnez pas cette option. Si vous sélectionnez cette option, les options de chiffrement dans la page **Options de sauvegarde** seront désactivées. Le chiffrement n'est pas pris en charge lors de l'ajout à un jeu de sauvegarde existant.  
  
    -   **Sauvegarder sur un nouveau support de sauvegarde et effacer tous les jeux de sauvegarde existants**  
  
         Pour cette option, entrez un nom dans la zone de texte **Nouveau nom du support de sauvegarde** et décrivez éventuellement le jeu de supports dans la zone de texte **Description du nouveau support de sauvegarde** .  
  
        > [!IMPORTANT]  
        >  Cette option est désactivée si vous avez sélectionné **URL** dans la page **Général** . Ces actions ne sont pas prises en charge pour la sauvegarde vers le stockage Windows Azure.  
  
14. Dans la section **Fiabilité** , vous pouvez activer les cases à cocher :  
  
    -   **Vérifier la sauvegarde en fin d'opération**;  
  
    -   **Effectuer une somme de contrôle avant d'écrire sur le support**et éventuellement **Continuer lors d'erreurs de somme de contrôle**. Pour plus d’informations sur les sommes de contrôle, consultez [Erreurs de support possibles pendant les opérations de sauvegarde et de restauration &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).  
  
15. Si vous effectuez la sauvegarde sur un lecteur de bande (spécifié dans la section **Destination** de la page **Général**), l’option **Décharger la bande après la sauvegarde** est active. Vous pouvez cliquer sur cette option pour activer l'option **Rembobiner la bande avant de décharger** .  
  
    > [!NOTE]  
    >  Les options de la section **Journal des transactions** sont inactives, à moins que vous ne sauvegardiez un journal des transactions (comme spécifié dans la section **Type de sauvegarde** de la page **Général** ).  
  
16. Pour afficher ou sélectionner les options de sauvegarde, cliquez sur **Options de sauvegarde** dans le volet **Sélectionner une page** .  
  
17. Spécifiez le moment où le jeu de sauvegarde va expirer et pourra être remplacé sans ignorer explicitement la vérification des données d'expiration :  
  
    -   Pour que le jeu de sauvegarde expire au bout d’un nombre de jours spécifique, cliquez sur **Après** (option par défaut) et entrez le nombre de jours souhaité pour l’expiration du jeu après sa création. Cette valeur doit être comprise entre 0 et 99999 jours ; une valeur de 0 jour signifie que le jeu de sauvegarde n'expirera jamais.  
  
         La valeur par défaut est définie dans l’option **Délai de rétention par défaut du support de sauvegarde (jours)** de la boîte de dialogue **Propriétés du serveur** (page Paramètres de base de données). Pour y accéder, cliquez avec le bouton droit sur le nom du serveur dans l’Explorateur d’objets et sélectionnez les propriétés. Ensuite, sélectionnez la page **Paramètres de base de données** .  
  
    -   Pour que le jeu de sauvegarde expire à une date spécifique, cliquez sur **Le**et entrez la date d'expiration souhaitée.  
  
         Pour plus d’informations sur les dates d’expiration des sauvegardes, consultez [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
18. [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] et versions ultérieures prennent en charge la [compression de la sauvegarde](backup-compression-sql-server.md). Par défaut, la compression d’une sauvegarde dépend de la valeur de l’option de configuration de serveur **Compression par défaut des sauvegardes** . Toutefois, quelle que soit la valeur par défaut actuelle au niveau du serveur, vous pouvez compresser une sauvegarde en activant **Compresser la sauvegarde**, et vous pouvez empêcher la compression en activant **Ne pas compresser la sauvegarde**.  
  
     **Pour afficher ou modifier la valeur par défaut de compression de la sauvegarde en cours**  
  
    -   [Afficher ou configurer la compression par défaut des sauvegardes (option de configuration de serveur)](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
19. Spécifiez si utiliser le chiffrement pour la sauvegarde. Sélectionnez l'algorithme de chiffrement à utiliser pour l'étape de chiffrement et fournissez un certificat ou une clé asymétrique dans la liste des certificats ou clés numériques existants. Le chiffrement est pris en charge dans SQL Server 2014 ou les versions ultérieures. Pour plus d’informations sur les options de chiffrement, consultez [Sauvegarder la base de données &#40;page Options de sauvegarde&#41;](back-up-database-backup-options-page.md).  
  
> [!NOTE]  
>  Vous pouvez également utiliser l'Assistant Plan de maintenance pour créer des sauvegardes de bases de données.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-full-database-backup"></a>Pour créer une sauvegarde de base de données complète  
  
1.  Exécutez l'instruction BACKUP DATABASE en spécifiant les éléments suivants :  
  
    -   le nom de la base de données à sauvegarder ;  
  
    -   l'unité de sauvegarde où est écrite la sauvegarde complète de la base de données.  
  
     La syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] de base nécessaire pour une sauvegarde de base de données complète est la suivante :  
  
     BACKUP DATABASE *database*  
  
     TO *unité_sauvegarde* [ **,**...*n* ]  
  
     [ WITH *options_with* [ **,**...*o* ] ] ;  
  
    |Option|Description|  
    |------------|-----------------|  
    |*database*|Base de données à sauvegarder|  
    |*unité_sauvegarde* [ **,**...*n* ]|Spécifie une liste de 1 à 64 unités de sauvegarde à utiliser pour l'opération de sauvegarde. Vous pouvez spécifier une unité de sauvegarde physique ou une unité de sauvegarde logique correspondante, si celle-ci est déjà définie. Pour spécifier une unité de sauvegarde physique, utilisez l'option DISK ou TAPE :<br /><br /> { DISK &#124; TAPE } **=***physical_backup_device_name*<br /><br /> Pour plus d’informations, consultez [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md).|  
    |WITH *options_with* [ **,**...*o* ]|Spécifie éventuellement une ou plusieurs options supplémentaires, *o*. Pour obtenir des informations de base sur les options, consultez l'étape 2.|  
  
2.  Spécifiez éventuellement une ou plusieurs options WITH. Quelques options WITH de base sont décrites ici. Pour plus d’informations sur toutes les options WITH, consultez [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
    -   Options WITH de base relatives au jeu de sauvegarde :  
  
         { COMPRESSION | NO_COMPRESSION }  
         Dans [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] et versions ultérieures uniquement, spécifie si la [compression de la sauvegarde](backup-compression-sql-server.md) est effectuée sur cette sauvegarde, remplaçant la valeur par défaut au niveau du serveur.  
  
         ENCRYPTION (ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY)  
         Dans SQL Server 2014 ou les versions ultérieures, spécifiez l'algorithme de chiffrement à utiliser, ainsi que le certificat ou la clé asymétrique pour sécuriser le chiffrement.  
  
         DESCRIPTION **=** { **'*`text`*'** | **@*** variable_texte* }  
         Spécifie le texte au format libre servant à décrire le jeu de sauvegarde. La chaîne peut compter jusqu'à 255 caractères.  
  
         NAME **=** { *backup_set_name* | **@***backup_set_name_var* }  
         Spécifie le nom du jeu de sauvegarde. Les noms peuvent contenir jusqu'à 128 caractères. Si l'option NAME n'est pas spécifiée, le nom reste vide.  
  
    -   Options WITH de base relatives au jeu de sauvegarde :  
  
         Par défaut, l'option BACKUP ajoute la sauvegarde à un support de sauvegarde existant, préservant les jeux de sauvegarde existants. Pour spécifier explicitement ceci, utilisez l'option NOINIT. Pour plus d’informations sur l’ajout à des jeux de sauvegarde existants, consultez [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
         Une autre méthode pour formater le support de sauvegarde consiste à utiliser l'option FORMAT :  
  
         FORMAT [ **,** MEDIANAME**=** { *nom_support* | **@***variable_nom_support* } ] [ **,** MEDIADESCRIPTION **=** { *text* | **@***variable_texte* } ]  
         Utilisez la clause FORMAT si vous utilisez le support pour la première fois ou si vous souhaitez écraser toutes les données existantes. Assignez éventuellement un nom et une description au nouveau support.  
  
        > [!IMPORTANT]  
        >  Soyez extrêmement vigilant lorsque vous utilisez la clause FORMAT de l'instruction BACKUP, car elle entraîne la destruction de toutes les sauvegardes préalablement stockées sur le support de sauvegarde.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
  
#### <a name="a-backing-up-to-a-disk-device"></a>A. Sauvegarde sur une unité de disque  
 L'exemple suivant sauvegarde entièrement la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sur disque, à l'aide de `FORMAT` , pour créer une nouveau jeu de supports.  
  
```tsql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH FORMAT,  
      MEDIANAME = 'Z_SQLServerBackups',  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="b-backing-up-to-a-tape-device"></a>B. Sauvegarde sur un périphérique à bandes  
 L'exemple suivant sauvegarde la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]complète sur bande, en ajoutant la sauvegarde aux sauvegardes précédentes.  
  
```tsql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO TAPE = '\\.\Tape0'  
   WITH NOINIT,  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="c-backing-up-to-a-logical-tape-device"></a>C. Sauvegarde sur un périphérique à bandes logique  
 L'exemple suivant crée une unité de sauvegarde logique pour un périphérique à bandes. Il sauvegarde ensuite la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] complète sur ce périphérique.  
  
```tsql  
-- Create a logical backup device,   
-- AdventureWorks2012_Bak_Tape, for tape device \\.\tape0.  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'AdventureWorks2012_Bak_Tape', '\\.\tape0'; USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO AdventureWorks2012_Bak_Tape  
   WITH FORMAT,  
      MEDIANAME = 'AdventureWorks2012_Bak_Tape',  
      MEDIADESCRIPTION = '\\.\tape0',   
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
  
1.  Utilisez le `Backup-SqlDatabase` applet de commande. Pour indiquer explicitement qu’il s’agit d’une sauvegarde complète de base de données, spécifiez la **- BackupAction** paramètre avec sa valeur par défaut, `Database`. Ce paramètre est facultatif pour les sauvegardes complètes de base de données.  
  
     L'exemple suivant crée une sauvegarde complète de la base de données `MyDB` à l'emplacement de sauvegarde par défaut de l'instance de serveur `Computer\Instance`. Cet exemple spécifie, de manière facultative, `-BackupAction Database`.  
  
    ```  
    --Enter this command at the PowerShell command prompt, C:\PS>  
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Database  
    ```  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Sauvegarder une base de données (SQL Server)](create-a-full-database-backup-sql-server.md)  
  
-   [Créer une sauvegarde différentielle de base de données &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
-   [Restaurer une sauvegarde de base de données &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [Restaurer une sauvegarde de base de données en mode de récupération simple &#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [Restaurer une base de données jusqu’au point d’échec en mode de récupération complète &#40;Transact-SQL&#41;](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [Restaurer une base de données à un nouvel emplacement &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md)  
  
-   [Utiliser l'Assistant Plan de maintenance](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](backup-overview-sql-server.md)   
 [Sauvegardes des journaux de transactions &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Sauvegarder la base de données &#40;page Général&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)   
 [Sauvegarder la base de données &#40;page Options de sauvegarde&#41;](back-up-database-backup-options-page.md)   
 [Sauvegardes différentielles &#40;SQL Server&#41;](differential-backups-sql-server.md)   
 [Sauvegardes complètes de bases de données &#40;SQL Server&#41;](full-database-backups-sql-server.md)  
  
  
