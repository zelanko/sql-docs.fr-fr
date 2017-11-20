---
title: "Sauvegarde et restauration de bases de données DQS | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: 
ms.component: data-quality-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6bab5e3ddb4473a949b12f0ce001a947262966c7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="backing-up-and-restoring-dqs-databases"></a>Sauvegarde et restauration de bases de données DQS
  Cette rubrique explique comment sauvegarder et restaurer les bases de données DQS.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Prérequis  
  
-   Vous devez connaître ou mémoriser le mot de passe de la clé principale de base de données que vous avez fourni pendant l'installation du serveur DQS.  
  
-   Vérifiez qu'aucune activité ou aucun processus n'est en cours d'exécution dans DQS. Pour ce faire, utilisez l'écran **Analyse des activités** . Pour plus d'informations sur l'utilisation de cet écran, consultez [Monitor DQS Activities](../data-quality-services/monitor-dqs-activities.md).  
  
-   Assurez-vous qu'aucun utilisateur n'est connecté au serveur DQS.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
  
-   Votre compte d'utilisateur Windows doit être membre du rôle serveur fixe sysadmin dans l'instance de SQL Server pour effectuer les opérations de sauvegarde et de restauration.  
  
-   Vous devez disposer du rôle dqs_administrator sur la base de données DQS_MAIN pour mettre fin à toutes les activités en cours d'exécution ou arrêter tous les processus en cours d'exécution dans DQS.  
  
##  <a name="BackupRestore"></a> Sauvegarder et restaurer des bases de données DQS  
  
1.  Démarrez Microsoft SQL Server Management Studio et connectez-vous à l'instance de SQL Server appropriée.  
  
2.  Dans l'Explorateur d'objets, développez le nœud **Bases de données** .  
  
3.  Sauvegardez la base de données DQS_STAGING_DATA. Pour obtenir des instructions pas à pas sur la sauvegarde d’une base de données SQL Server, consultez [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
4.  Sauvegardez la base de données DQS_PROJECTS.  
  
5.  Sauvegardez la base de données DQS_MAIN.  
  
6.  Déconnectez-vous de l'instance actuelle de SQL Server, et connectez-vous à l'instance de SQL Server où vous voulez restaurer ces bases de données.  
  
7.  Restaurez la base de données DQS_MAIN. Pour obtenir des instructions pas à pas sur la restauration d’une base de données SQL Server, consultez [Restaurer une sauvegarde de base de données à l’aide de SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).  
  
8.  Restaurez la base de données DQS_PROJECTS.  
  
9. Restaurez la base de données DQS_STAGING_DATA.  
  
10. Dans l'Explorateur d'objets, cliquez avec le bouton droit sur le serveur, puis cliquez sur **Nouvelle requête**.  
  
11. Dans la fenêtre de l’éditeur de requête, copiez les instructions SQL suivantes et remplacez *\<PASSWORD>* par le mot de passe que vous avez fourni pendant l’installation de DQS pour la clé principale de base de données :  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
  
    ```  
  
12. Appuyez sur F5 pour exécuter les instructions. Consultez le volet de **résultats** pour vérifier que les instructions ont été correctement exécutées.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les bases de données DQS](../data-quality-services/manage-dqs-databases.md)  
  
  

