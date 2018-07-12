---
title: Sauvegarder un journal des transactions (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transaction log backups [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- backing up transaction logs [SQL Server], SQL Server Management Studio
ms.assetid: 3426b5eb-6327-4c7f-88aa-37030be69fbf
caps.latest.revision: 44
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d4fa8ba90a87dc6444d9181e2b724201a130880e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178136"
---
# <a name="back-up-a-transaction-log-sql-server"></a>Sauvegarder un journal des transactions (SQL Server)
  Cette rubrique explique comment sauvegarder un journal des transactions dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de PowerShell.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour sauvegarder un journal des transactions, à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
    > [!NOTE]  
    >  Vous pouvez également utiliser l'[Assistant Plan de maintenance](../maintenance-plans/use-the-maintenance-plan-wizard.md)pour créer des sauvegardes.  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   L'instruction BACKUP n'est pas autorisée dans une transaction explicite ou implicite.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Si une base de données est configurée pour le mode de récupération complète ou le mode de récupération utilisant les journaux de transactions, vous devez sauvegarder le journal des transactions assez régulièrement pour protéger vos données et éviter une saturation de ce dernier. Cela tronque le journal et prend en charge la restauration de la base de données à un point précis dans le temps.  
  
-   Par défaut, chaque opération de sauvegarde réussie ajoute une entrée au journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et au journal des événements système. Si vous sauvegardez très fréquemment le journal, ces messages de réussite peuvent rapidement s'accumuler, créer des journaux d'erreurs très volumineux et compliquer la recherche d'autres messages. Dans de tels cas, vous pouvez supprimer ces entrées de journal en utilisant l'indicateur de trace 3226 si aucun de vos scripts ne dépend de ces entrées. Pour plus d’informations, consultez [Indicateurs de trace &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Les autorisations BACKUP DATABASE et BACKUP LOG reviennent par défaut aux membres du rôle serveur fixe **sysadmin** et des rôles de base de données fixes **db_owner** et **db_backupoperator** .  
  
 Des problèmes de propriété et d'autorisations sur le fichier physique de l'unité de sauvegarde sont susceptibles de perturber une opération de sauvegarde. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être en mesure de lire et d'écrire sur l'unité ; le compte sous lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute doit avoir des autorisations d'écriture. Toutefois, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), qui ajoute une entrée pour une unité de sauvegarde dans les tables système, ne vérifie pas les autorisations d’accès au fichier. De tels problèmes pour le fichier physique de l'unité de sauvegarde peuvent n'apparaître que lorsque la ressource physique est sollicitée au moment de la sauvegarde ou de la restauration.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-back-up-a-transaction-log"></a>Pour sauvegarder un journal des transactions  
  
1.  Après vous être connecté à l'instance appropriée du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dans l'Explorateur d'objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Bases de données**puis, selon la base de données, sélectionnez une base de données utilisateur ou développez **Bases de données système** et sélectionnez une base de données système.  
  
3.  Cliquez avec le bouton droit sur la base de données, pointez sur **Tâches**, puis cliquez sur **Sauvegarder**. La boîte de dialogue **Sauvegarder la base de données** s'affiche.  
  
4.  Dans la zone de liste **Base de données** , vérifiez le nom de la base de données. Vous pouvez éventuellement sélectionner une autre base de données dans la liste.  
  
5.  Vérifiez que le mode de récupération est **FULL** ou **BULK_LOGGED**.  
  
6.  Dans la zone de liste **Type de sauvegarde** , sélectionnez **Journal des transactions**.  
  
7.  Vous pouvez si vous le souhaitez sélectionner **Sauvegarde de copie uniquement** pour créer une sauvegarde de copie uniquement. Une *sauvegarde de copie uniquement* est une sauvegarde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indépendante du mécanisme des sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conventionnelles. Pour plus d’informations, consultez [Sauvegardes de copie uniquement &#40;SQL Server&#41;](copy-only-backups-sql-server.md).  
  
    > [!NOTE]  
    >  Quand l’option **Différentielle** est sélectionnée, vous ne pouvez pas créer de sauvegarde de copie uniquement.  
  
8.  Acceptez le nom du jeu de sauvegarde par défaut proposé dans la zone de texte **Nom** , ou attribuez-lui un autre nom.  
  
9. Dans la zone de texte **Description** , vous avez la possibilité de saisir une description du jeu de sauvegarde.  
  
10. Indiquez quand le jeu de sauvegarde arrivera à expiration :  
  
    -   Pour que le jeu de sauvegarde expire au bout d’un nombre de jours spécifique, cliquez sur **Après** (option par défaut) et entrez le nombre de jours souhaité pour l’expiration du jeu après sa création. Cette valeur doit être comprise entre 0 et 99999 jours ; une valeur de 0 jour signifie que le jeu de sauvegarde n'expirera jamais.  
  
         La valeur par défaut est définie dans l’option **Délai de rétention par défaut du support de sauvegarde (jours)** de la boîte de dialogue **Propriétés du serveur** (page**Paramètres de base de données** ). Pour accéder à cette base de données, cliquez avec le bouton droit sur le nom du serveur dans l’Explorateur d’objets et sélectionnez Propriétés. Ensuite, sélectionnez la page **Paramètres de base de données** .  
  
    -   Pour que le jeu de sauvegarde expire à une date spécifique, cliquez sur **Le**et entrez la date d'expiration souhaitée.  
  
11. Choisissez le type de destination de la sauvegarde en cliquant sur **Disque**, **URL** ou **Bande**. Pour sélectionner les chemins d'accès à 64 lecteurs de bande ou de disque au maximum contenant un seul support de sauvegarde, cliquez sur **Ajouter**. Les chemins d'accès sélectionnés apparaissent dans la zone de liste **Sauvegarde sur** .  
  
     Pour supprimer une destination de sauvegarde, sélectionnez-la, puis cliquez sur **Supprimer**. Pour afficher le contenu d'une destination de sauvegarde, sélectionnez-la, puis cliquez sur **Sommaire**.  
  
12. Pour afficher ou sélectionner les options avancées, cliquez sur **Options** dans le volet **Sélectionner une page** .  
  
13. Sélectionnez une option **Remplacer le support** en cliquant sur un des éléments suivants :  
  
    -   **Sauvegarder sur le support de sauvegarde existant**  
  
         Pour cette option, cliquez sur **Ajouter au jeu de sauvegarde existant** ou sur **Remplacer tous les jeux de sauvegarde existants**. Pour plus d’informations, consultez [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
         Vous pouvez aussi activer la case à cocher **Vérifier le nom du support de sauvegarde et la date d'expiration du jeu de sauvegarde** pour forcer l'opération de sauvegarde à vérifier la date et l'heure de l'expiration du jeu de supports ou du jeu de sauvegarde.  
  
         Vous pouvez éventuellement entrer un nom dans la zone de texte **Nom du support de sauvegarde** . Si aucun nom n'est spécifié, un support de sauvegarde avec un nom vide est créé. Si vous spécifiez un nom pour le support de sauvegarde, ce support (bande ou disque) est vérifié pour voir si le nom réel correspond bien au nom que vous entrez ici.  
  
         Si vous n'entrez pas de nom et que vous activez la case à cocher pour demander la vérification par rapport au support, le nom du support sera également vide sur le support.  
  
    -   **Sauvegarder sur un nouveau support de sauvegarde et effacer tous les jeux de sauvegarde existants**  
  
         Pour cette option, entrez un nom dans la zone de texte **Nouveau nom du support de sauvegarde** et décrivez éventuellement le jeu de supports dans la zone de texte **Description du nouveau support de sauvegarde** . Pour plus d’informations, consultez [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).  
  
14. Dans la section **Fiabilité** , vous pouvez éventuellement activer les cases à cocher :  
  
    -   **Vérifier la sauvegarde en fin d'opération**;  
  
    -   **Effectuer une somme de contrôle avant d'écrire sur le support**et éventuellement **Continuer lors d'erreurs de somme de contrôle**. Pour plus d’informations sur les sommes de contrôle, consultez [Erreurs de support possibles pendant les opérations de sauvegarde et de restauration &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).  
  
15. Dans la section **Journal des transactions** :  
  
    -   Pour les sauvegardes normales du journal, conservez la sélection par défaut, **Tronquer le journal des transactions en supprimant les entrées inactives**.  
  
    -   Pour sauvegarder la fin du journal (autrement dit le journal actif), cochez la case **Sauvegarder la fin du journal et laisser la base de données dans l’état de restauration**.  
  
         Une sauvegarde de la fin du journal est effectuée après une défaillance pour éviter de perdre des données. Sauvegardez le journal actif (sauvegarde de la fin du journal) après une défaillance, avant de commencer la restauration de la base de données ou en cas de basculement sur une base de données secondaire. Sélectionner cette option équivaut à spécifier l'option NORECOVERY dans l'instruction BACKUP LOG de Transact-SQL. Pour plus d’informations sur les sauvegardes de la fin du journal, consultez [Sauvegardes de la fin du journal &#40;SQL Server&#41;](tail-log-backups-sql-server.md).  
  
16. Si vous effectuez la sauvegarde sur un lecteur de bande (spécifié dans la section **Destination** de la page **Général** ), l’option **Décharger la bande après la sauvegarde** est active. Vous pouvez cliquer sur cette option pour activer l'option **Rembobiner la bande avant de décharger** .  
  
17. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] et versions ultérieures prennent en charge la [compression de la sauvegarde](backup-compression-sql-server.md). Par défaut, la compression d’une sauvegarde dépend de la valeur de l’option de configuration de serveur **Compression par défaut des sauvegardes** . Toutefois, quelle que soit la valeur par défaut actuelle au niveau du serveur, vous pouvez compresser une sauvegarde en activant **Compresser la sauvegarde**, et vous pouvez empêcher la compression en activant **Ne pas compresser la sauvegarde**.  
  
     **Pour consulter la valeur par défaut de compression de la sauvegarde actuelle**  
  
    -   [Afficher ou configurer l'option de configuration du serveur valeur par défaut de compression de la sauvegarde](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
 **Chiffrement**  
  
 Pour chiffrer le fichier de sauvegarde, activez la case à cocher **Chiffrer le fichier de sauvegarde** . Sélectionnez l'algorithme de chiffrement à utiliser pour chiffrer le fichier de sauvegarde et fournissez un certificat ou une clé asymétrique. Les algorithmes disponibles pour le chiffrement sont :  
  
-   AES 128  
  
-   AES 192  
  
-   AES 256  
  
-   Triple DES  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-back-up-a-transaction-log"></a>Pour sauvegarder un journal des transactions  
  
1.  Exécutez l'instruction BACKUP LOG pour sauvegarder le journal des transactions, en spécifiant :  
  
    -   Le nom de la base de données à laquelle appartient le journal des transactions à sauvegarder.  
  
    -   l'unité de sauvegarde où sera écrite la sauvegarde du journal des transactions.  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
  
> [!IMPORTANT]  
>  Cet exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] , qui fait appel au mode de récupération simple. Pour autoriser les sauvegardes de fichier journal, avant d'effectuer une sauvegarde complète de base de données, la base de données a été configurée pour utiliser le mode de récupération complète. Pour plus d’informations, consultez [Afficher ou modifier le mode de récupération d’une base de données &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).  
  
 L'exemple suivant crée une sauvegarde du journal des transactions pour la base de données [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sur l'unité de sauvegarde nommée qui a été précédemment créée, `MyAdvWorks_FullRM_log1`.  
  
```tsql  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1;  
GO  
```  
  
##  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
  
1.  Utilisez l'applet de commande `Backup-SqlDatabase` et spécifiez `Log` comme valeur du paramètre `-BackupAction`.  
  
     L'exemple suivant crée une sauvegarde de fichier journal de la base de données `MyDB` à l'emplacement de sauvegarde par défaut de l'instance de serveur `Computer\Instance`.  
  
    ```  
    --Enter this command at the PowerShell command prompt, C:\PS>  
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Log  
    ```  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Restaurer une sauvegarde de journal des transactions &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
-   [Restaurer une base de données SQL Server jusqu’à une limite dans le temps &#40;mode de récupération complète&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [Résoudre les problèmes liés à un journal des transactions saturé &#40;erreur SQL Server 9002&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [Appliquer les sauvegardes du journal des transactions &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [Plans de maintenance](../maintenance-plans/maintenance-plans.md)   
 [Sauvegardes de fichiers complètes &#40;SQL Server&#41;](full-file-backups-sql-server.md)  
  
  
