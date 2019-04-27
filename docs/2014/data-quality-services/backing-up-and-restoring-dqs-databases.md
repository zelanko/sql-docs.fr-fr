---
title: Sauvegarde et restauration de bases de données DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c139e5e9487dc703b3a24b159e17c7495fb88c3e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62755789"
---
# <a name="backing-up-and-restoring-dqs-databases"></a>Sauvegarde et restauration de bases de données DQS
  Cette rubrique explique comment sauvegarder et restaurer les bases de données DQS.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   Vous devez connaître ou mémoriser le mot de passe de la clé principale de base de données que vous avez fournie pendant l'installation du serveur DQS.  
  
-   Vérifiez qu'aucune activité ou aucun processus n'est en cours d'exécution dans DQS. Pour ce faire, utilisez l'écran **Analyse des activités** . Pour plus d'informations sur l'utilisation de cet écran, consultez [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md).  
  
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
  
7.  Restaurez la base de données DQS_MAIN. Pour obtenir des instructions pas à pas restaurer une base de données SQL Server, consultez [restaurer une sauvegarde de base de données &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).  
  
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
 [Manage DQS Databases](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
