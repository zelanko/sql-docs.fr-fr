---
title: Supprimer une base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database removal [SQL Server], SQL Server Management Studio
- removing databases
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- database removal [SQL Server]
ms.assetid: 1fd8c0f5-03e1-449a-af45-b8cacb479d9c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ffda3be2194b26b46f9633c3bdf76d60d36ce73c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62871914"
---
# <a name="delete-a-database"></a>Supprimer une base de données
  Cette rubrique explique comment supprimer une base de données définie par l'utilisateur dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Conditions préalables](#Prerequisites)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après la suppression d’une base de données](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Les bases de données système ne peuvent pas être supprimées.  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   Supprimez les instantanés de la base de données qui existent. Pour plus d’informations, consultez [Supprimer un instantané de base de données &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).  
  
-   Si la base de données intervient dans l'envoi de journaux, supprimez l'envoi de journaux.  
  
-   Si la base de données est publiée pour une réplication transactionnelle, ou encore publiée ou souscrite pour une réplication de fusion, supprimez la réplication.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Effectuez une sauvegarde complète de la base de données. Vous ne pouvez recréer une base de données supprimée qu'en restaurant une copie de sauvegarde.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Pour exécuter DROP DATABASE, un utilisateur doit au moins disposer de l'autorisation CONTROL sur la base de données.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-database"></a>Pour supprimer une base de données  
  
1.  Dans **l’Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], puis développez-la.  
  
2.  Développez le dossier **Bases de données**, cliquez avec le bouton droit sur la base de données à supprimer, puis cliquez sur **Supprimer**.  
  
3.  Vérifiez que la base de données correcte est sélectionnée, puis cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-database"></a>Pour supprimer une base de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple suivant supprime les bases de données `Sales` et `NewSales` .  
  
```sql  
USE master ;  
GO  
DROP DATABASE Sales, NewSales ;  
GO  
```  
  
##  <a name="FollowUp"></a> Suivi : Après la suppression d’une base de données  
 Sauvegardez la base de données **master** . Si vous devez restaurer la base de données **master** , toutes les bases de données supprimées depuis la dernière sauvegarde de **master** seront encore référencées dans les vues du catalogue système, ce qui risque de générer des messages d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
