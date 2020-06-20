---
title: Sauvegarder des fichiers et des groupes de fichiers (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up filegroups [SQL Server]
- file backups [SQL Server], how-to topics
- backing up files [SQL Server]
- backups [SQL Server], creating
- filegroups [SQL Server], backing up
ms.assetid: a0d3a567-7d8b-4cfe-a505-d197b9a51f70
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7affc90b064febaa70e0a67108074f412b4bbf00
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84959639"
---
# <a name="back-up-files-and-filegroups-sql-server"></a>Sauvegarder des fichiers et des groupes de fichiers (SQL Server)
  Cette rubrique explique comment sauvegarder des fichiers et des groupes de fichiers dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de PowerShell. Lorsque la taille de la base de données et les exigences en matière de performances rendent impraticable une sauvegarde complète de la base de données, créez une sauvegarde de fichiers. Une *sauvegarde de fichiers* contient toutes les données dans un ou plusieurs fichiers (ou groupes de fichiers). Pour plus d’informations sur les sauvegardes de fichiers, consultez [Sauvegardes de fichiers complètes &#40;SQL Server&#41;](full-file-backups-sql-server.md) et [Sauvegardes différentielles &#40;SQL Server&#41;](differential-backups-sql-server.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour sauvegarder des groupes de fichiers et des fichiers, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   L'instruction BACKUP n'est pas autorisée dans une transaction explicite ou implicite.  
  
-   En mode de récupération simple, vous devez sauvegarder conjointement tous les fichiers en lecture-écriture. Cela permet de garantir la restauration de la base de données dans un état cohérent dans le temps. Plutôt que de spécifier individuellement chaque fichier ou groupe de fichier en lecture-écriture, utilisez l'option READ_WRITE_FILEGROUPS. Cette option sauvegarde tous les groupes de fichiers en lecture-écriture dans la base de données. Une sauvegarde créée en spécifiant READ_WRITE_FILEGROUPS est appelée *sauvegarde partielle*. Pour plus d’informations, consultez [Sauvegardes partielles &#40;SQL Server&#41;](partial-backups-sql-server.md).  
  
-   Pour plus d'informations sur les limitations et les restrictions, consultez [Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](backup-overview-sql-server.md).  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
  
-   Par défaut, chaque opération de sauvegarde réussie ajoute une entrée au journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et au journal des événements système. Si vous sauvegardez très fréquemment le journal, ces messages de réussite peuvent rapidement s'accumuler, créer des journaux d'erreurs très volumineux et compliquer la recherche d'autres messages. Dans de tels cas, vous pouvez supprimer ces entrées de journal en utilisant l'indicateur de trace 3226 si aucun de vos scripts ne dépend de ces entrées. Pour plus d’informations, consultez [Indicateurs de trace &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Les autorisations BACKUP DATABASE et BACKUP LOG reviennent par défaut aux membres du rôle serveur fixe **sysadmin** et des rôles de base de données fixes **db_owner** et **db_backupoperator** .  
  
 Des problèmes de propriété et d'autorisations sur le fichier physique de l'unité de sauvegarde sont susceptibles de perturber une opération de sauvegarde. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être en mesure de lire et d'écrire sur l'unité ; le compte sous lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute doit avoir des autorisations d'écriture. Toutefois, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), qui ajoute une entrée pour une unité de sauvegarde dans les tables système, ne vérifie pas les autorisations d’accès au fichier. De tels problèmes pour le fichier physique de l'unité de sauvegarde peuvent n'apparaître que lorsque la ressource physique est sollicitée au moment de la sauvegarde ou de la restauration.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-back-up-database-files-and-filegroups"></a>Pour sauvegarder des groupes de fichiers et des fichiers de base de données  
  
1.  Après vous être connecté à l'instance appropriée du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dans l'Explorateur d'objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Bases de données**puis, selon la base de données, sélectionnez une base de données utilisateur ou développez **Bases de données système** et sélectionnez une base de données système.  
  
3.  Cliquez avec le bouton droit sur la base de données, pointez sur **Tâches**, puis cliquez sur **Sauvegarder**. La boîte de dialogue **Sauvegarder la base de données** s'affiche.  
  
4.  Dans la liste **Base de données** , vérifiez le nom de la base de données. Vous pouvez éventuellement sélectionner une autre base de données dans la liste.  
  
5.  Dans la liste **Type de sauvegarde** , sélectionnez **Complète** ou **Différentielle**.  
  
6.  Pour l'option **Composant de sauvegarde** , cliquez sur **Fichier et groupes de fichiers**.  
  
7.  Dans la boîte de dialogue **Sélection de fichiers et de groupes de fichiers** , sélectionnez les fichiers et les groupes de fichiers que vous voulez sauvegarder. Vous pouvez sélectionner un ou plusieurs fichiers individuellement, ou vous pouvez activer la case qui permet de sélectionner automatiquement tous les fichiers d'un groupe de fichiers.  
  
8.  Acceptez le nom du jeu de sauvegarde par défaut proposé dans la zone de texte **Nom** , ou attribuez-lui un autre nom.  
  
9. Dans la zone de texte **Description** , vous avez la possibilité de saisir une description du jeu de sauvegarde.  
  
10. Indiquez quand le jeu de sauvegarde arrivera à expiration :  
  
    -   Pour que le jeu de sauvegarde expire au bout d’un certain nombre de jours, cliquez sur **Après** (option par défaut). Ensuite, entrez le nombre de jours suivant la création du jeu où le jeu expirera. Cette valeur doit être comprise entre 0 et 99999 jours ; une valeur de 0 jour signifie que le jeu de sauvegarde n'expirera jamais.  
  
         La valeur par défaut est définie dans l’option **Délai de rétention par défaut du support de sauvegarde (jours)** de la boîte de dialogue **Propriétés du serveur** (page**Paramètres de base de données** ). Pour accéder à cette option, cliquez avec le bouton droit sur le nom du serveur dans l’Explorateur d’objets et sélectionnez les propriétés ; sélectionnez ensuite la page **Paramètres de base de données** .  
  
    -   Pour que le jeu de sauvegarde expire à une date spécifique, cliquez sur **Le**et entrez la date d'expiration souhaitée.  
  
11. Choisissez le type de destination de la sauvegarde : **Disque** ou **Bande**. Pour sélectionner les chemins d'accès de 64 lecteurs de bande ou disques (maximum) contenant un support de sauvegarde unique, cliquez sur **Ajouter**. Les chemins sélectionnés sont affichés dans la liste **Sauvegarde sur** .  
  
    > [!NOTE]  
    >  Pour supprimer une destination de sauvegarde, sélectionnez-la, puis cliquez sur **Supprimer**. Pour afficher le contenu d'une destination de sauvegarde, sélectionnez-la, puis cliquez sur **Sommaire**.  
  
12. Pour afficher ou sélectionner les options avancées, cliquez sur **Options** dans le volet **Sélectionner une page** .  
  
13. Sélectionnez une option **Remplacer le support** en cliquant sur un des éléments suivants :  
  
    -   **Sauvegarder sur le support de sauvegarde existant**  
  
         Pour cette option, cliquez sur **Ajouter au jeu de sauvegarde existant** ou sur **Remplacer tous les jeux de sauvegarde existants**. Pour plus d’informations sur la sauvegarde sur un jeu de supports existant, consultez [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
         Vous pouvez aussi activer la case à cocher **Vérifier le nom du support de sauvegarde et la date d'expiration du jeu de sauvegarde** pour forcer l'opération de sauvegarde à vérifier la date et l'heure de l'expiration du jeu de supports ou du jeu de sauvegarde.  
  
         Vous pouvez éventuellement entrer un nom dans la zone de texte **Nom du support de sauvegarde** . Si aucun nom n'est spécifié, un support de sauvegarde avec un nom vide est créé. Si vous spécifiez un nom pour le jeu de sauvegarde, le support (bande ou disque) est vérifié pour voir si le nom réel correspond bien au nom que vous entrez ici.  
  
         Si vous n'entrez pas de nom et que vous activez la case à cocher pour demander la vérification par rapport au support, le nom du support sera également vide sur le support.  
  
    -   **Sauvegarder sur un nouveau support de sauvegarde et effacer tous les jeux de sauvegarde existants**  
  
         Pour cette option, entrez un nom dans la zone de texte **Nouveau nom du support de sauvegarde** et décrivez éventuellement le jeu de supports dans la zone de texte **Description du nouveau support de sauvegarde** . Pour plus d’informations sur la création d’un jeu de supports existant, consultez [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
14. Dans la section **fiabilité** , vérifiez éventuellement :  
  
    -   **Vérifier la sauvegarde en fin d'opération**;  
  
    -   **Effectuer une somme de contrôle avant d'écrire sur le support**et éventuellement **Continuer lors d'erreurs de somme de contrôle**. Pour plus d’informations sur les sommes de contrôle, consultez [Erreurs de support possibles pendant les opérations de sauvegarde et de restauration &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).  
  
15. Si vous effectuez la sauvegarde sur un lecteur de bande (spécifié dans la section **Destination** de la page **Général** ), l’option **Décharger la bande après la sauvegarde** est active. Cliquer sur cette option active l'option **Rembobiner la bande avant de décharger** .  
  
    > [!NOTE]  
    >  Les options de la section **Journal des transactions** sont inactives, à moins que vous ne sauvegardiez un journal des transactions (comme spécifié dans la section **Type de sauvegarde** de la page **Général** ).  
  
16. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] et les versions ultérieures prennent en charge la [compression de la sauvegarde](backup-compression-sql-server.md). Par défaut, la compression d’une sauvegarde dépend de la valeur de l’option de configuration de serveur **Compression par défaut des sauvegardes** . Toutefois, quelle que soit la valeur par défaut actuelle au niveau du serveur, vous pouvez compresser une sauvegarde en activant **Compresser la sauvegarde**, et vous pouvez empêcher la compression en activant **Ne pas compresser la sauvegarde**.  
  
     **Pour consulter la valeur par défaut de compression de la sauvegarde actuelle**  
  
    -   [Afficher ou configurer la compression par défaut des sauvegardes (option de configuration de serveur)](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-back-up-files-and-filegroups"></a>Pour sauvegarder les fichiers et groupes de fichiers  
  
1.  Pour créer une sauvegarde de fichier ou de groupe de fichiers, utilisez une instruction [BACKUP DATABASE <fichier_ou_groupe_de_fichiers>](/sql/t-sql/statements/backup-transact-sql). Au minimum, cette instruction doit spécifier les actions suivantes :  
  
    -   Nom de la base de données.  
  
    -   Clause FILE ou FILEGROUP pour chaque fichier ou groupe de fichiers, respectivement.  
  
    -   L’unité de sauvegarde où sera écrite la sauvegarde complète.  
  
     La syntaxe de base [!INCLUDE[tsql](../../includes/tsql-md.md)] d'une sauvegarde de fichiers est la suivante :  
  
     BACKUP DATABASE *database*  
  
     { FILE **=** _nom_fichier_logique_ | FILEGROUP **=** _nom_groupe_fichiers_logique_ } [ **,** ...*f* ]  
  
     TO *unité_sauvegarde* [ **,** ...*n* ]  
  
     [ WITH *options_with* [ **,** ...*o* ] ] ;  
  
    |Option|Description|  
    |------------|-----------------|  
    |*database*|Correspond à la base de données à partir de laquelle va être opérée la sauvegarde du journal des transactions, c'est à dire la sauvegarde complète ou partielle.|  
    |FILE **=** _nom_fichier_logique_|Indique le nom logique d'un fichier à inclure dans la sauvegarde de fichiers.|  
    |FILEGROUP **=** _nom_groupe_fichiers_logique_|Indique le nom logique d'un groupe de fichiers à inclure dans la sauvegarde de fichiers. En mode de récupération simple, la sauvegarde d'un groupe de fichiers n'est autorisée que pour un groupe de fichiers en lecture seule.|  
    |[ **,** ...*f* ]|Espace réservé indiquant qu'il est possible de spécifier plusieurs fichiers et groupes de fichiers. Le nombre de fichiers ou de groupes de fichiers est illimité.|  
    |*unité_sauvegarde* [ **,** ...*n* ]|Spécifie une liste de 1 à 64 unités de sauvegarde à utiliser pour l'opération de sauvegarde. Vous pouvez spécifier une unité de sauvegarde physique ou une unité de sauvegarde logique correspondante, si celle-ci est déjà définie. Pour spécifier une unité de sauvegarde physique, utilisez l'option DISK ou TAPE :<br /><br /> { DISK &#124; TAPE } **=** _nom_unité_sauvegarde_physique_<br /><br /> Pour plus d’informations, consultez [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md).|  
    |WITH *options_with* [ **,** ...*o* ]|Spécifie, éventuellement, une ou plusieurs options supplémentaires telles que DIFFERENTIAL.<br /><br /> Remarque : une sauvegarde différentielle de fichiers requiert une sauvegarde complète de fichiers comme base. Pour plus d’informations, consultez [Créer une sauvegarde différentielle de base de données &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md).|  
  
2.  En mode de restauration complète, vous devez aussi sauvegarder le journal des transactions. Pour utiliser un jeu complet de sauvegardes de fichiers complètes afin de restaurer une base de données, vous devez aussi disposer de suffisamment de sauvegardes de journal pour couvrir toutes les sauvegardes de fichiers depuis la première sauvegarde de fichiers. Pour plus d’informations, consultez [Sauvegarder un journal des transactions &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Exemples (Transact-SQL)  
 Dans les exemples suivants, vous procédez à une sauvegarde d'un ou plusieurs fichiers des groupes de fichiers secondaires de la base de données `Sales` . Cette base de données fait appel au mode de restauration complète et contient les groupes de fichiers secondaires suivants :  
  
-   Un groupe de fichiers nommé `SalesGroup1` avec les fichiers `SGrp1Fi1` et `SGrp1Fi2`.  
  
-   Un groupe de fichiers nommé `SalesGroup2` avec les fichiers `SGrp2Fi1` et `SGrp2Fi2`.  
  
#### <a name="a-creating-a-file-backup-of-two-files"></a>R. Création d'une sauvegarde de fichiers de deux fichiers  
 Dans l'exemple suivant, vous créez une sauvegarde de fichiers différentiel contenant seulement le fichier `SGrp1Fi2` du `SalesGroup1` et le fichier `SGrp2Fi2` du groupe de fichiers `SalesGroup2` .  
  
```sql  
--Backup the files in the SalesGroup1 secondary filegroup.  
BACKUP DATABASE Sales  
   FILE = 'SGrp1Fi2',   
   FILE = 'SGrp2Fi2'   
   TO DISK = 'G:\SQL Server Backups\Sales\SalesGroup1.bck';  
GO  
```  
  
#### <a name="b-creating-a-full-file-backup-of-the-secondary-filegroups"></a>B. Création d'une sauvegarde de fichiers complète des groupes de fichiers secondaires  
 L'exemple suivant crée une sauvegarde complète de tous les fichiers se trouvant dans les deux groupes de fichiers secondaires.  
  
```sql  
--Back up the files in SalesGroup1.  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'C:\MySQLServer\Backups\Sales\SalesFiles.bck';  
GO  
```  
  
#### <a name="c-creating-a-differential-file-backup-of-the-secondary-filegroups"></a>C. Création d'une sauvegarde de fichiers différentielle des groupes de fichiers secondaires  
 L'exemple suivant crée une sauvegarde différentielle de tous les fichiers se trouvant dans les deux groupes de fichiers secondaires.  
  
```sql  
--Back up the files in SalesGroup1.  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'C:\MySQLServer\Backups\Sales\SalesFiles.bck'  
   WITH   
      DIFFERENTIAL;  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Utilisation de PowerShell  
  
Utilisez l'applet de commande `Backup-SqlDatabase` et spécifiez `Files` comme valeur du paramètre `-BackupAction`. Spécifiez également l'un des paramètres suivants :  
  
    -   Pour sauvegarder un fichier spécifique, spécifiez le `-DatabaseFile` paramètre de *chaîne* , où *String* représente un ou plusieurs fichiers de base de données à sauvegarder.  
  
    -   Pour sauvegarder tous les fichiers d’un groupe de fichiers donné, spécifiez le `-DatabaseFileGroup` paramètre *String* , où *String* représente un ou plusieurs groupes de fichiers de base de données à sauvegarder.  
  
     L'exemple suivant crée une sauvegarde complète de tous les fichiers dans les groupes de fichiers secondaires 'FileGroup1' et 'FileGroup2' dans la base de données `MyDB` . Les sauvegardes sont créées à l’emplacement de sauvegarde par défaut de l’instance de serveur `Computer\Instance`.  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Files -DatabaseFileGroup "FileGroup1","FileGroup2"  
    ```  
  
Pour configurer et utiliser le fournisseur de SQL Server PowerShell, consultez [SQL Server PowerShell Provider](../../powershell/sql-server-powershell-provider.md).
  
## <a name="see-also"></a> Voir aussi  
 [Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](backup-overview-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Historique de sauvegarde et informations d’en-tête &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md)   
 [Sauvegarder la base de données &#40;page Général&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)   
 [Sauvegarder la base de données &#40;page Options de sauvegarde&#41;](back-up-database-backup-options-page.md)   
 [Sauvegardes de fichiers complètes &#40;SQL Server&#41;](full-file-backups-sql-server.md)   
 [Sauvegardes différentielles &#40;SQL Server&#41;](differential-backups-sql-server.md)   
 [Restaurations de fichiers &#40;mode de récupération complète&#41;](file-restores-full-recovery-model.md)   
 [Restaurations de fichiers &#40;mode de récupération simple&#41;](file-restores-simple-recovery-model.md)  
  
  
