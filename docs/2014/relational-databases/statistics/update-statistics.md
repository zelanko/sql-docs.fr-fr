---
title: Mettre à jour les statistiques | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- updating statistics
- statistics [SQL Server], updating
ms.assetid: 4b97c0b4-03ff-4cfb-9c3f-3b33290b7a2c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d83dcaf8ea6f674ae1086d2d02f9423a3bb98358
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053419"
---
# <a name="update-statistics"></a>Mettre à jour les statistiques
  Vous pouvez mettre à jour les statistiques d'optimisation de requête sur une table ou une vue indexée dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Par défaut, l'optimiseur de requête met à jour les statistiques en fonction des besoins afin d'améliorer le plan de requête ; dans certains cas, vous pouvez optimiser les performances des requêtes en utilisant UPDATE STATISTICS ou la procédure stockée `sp_updatestats` pour mettre à jour les statistiques de manière plus fréquente qu'avec les mises à jour par défaut.  
  
 La mise à jour des statistiques est l'assurance que les requêtes sont compilées avec des statistiques à jour. Toutefois, la mise à jour des statistiques entraîne une recompilation des requêtes. À ce titre, il est déconseillé de mettre à jour les statistiques de façon trop régulière eu égard aux performances. Un compromis doit être trouvé entre le souhait d'améliorer les plans de requête et le temps nécessaire à la recompilation des requêtes. Ce compromis peut varier en fonction de votre application. UPDATE STATISTICS peut utiliser tempdb pour trier l’échantillon de lignes à des fins statistiques.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour mettre à jour un objet de statistiques, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 L'utilisation d'UPDATE STATISTICS ou l'apport de modifications par le biais de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]exige l'autorisation ALTER sur la table ou la vue. En cas d’utilisation de `sp_updatestats`, nécessite l’appartenance au rôle serveur fixe **sysadmin** ou la propriété de la base de données (**dbo**).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-update-a-statistics-object"></a>Pour mettre à jour un objet de statistiques  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer la base de données dans laquelle vous souhaitez mettre à jour la statistique.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Tables** .  
  
3.  Cliquez sur le signe plus (+) pour développer la table dans laquelle vous souhaitez mettre à jour la statistique.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Statistiques** .  
  
5.  Cliquez avec le bouton droit sur l’objet de statistiques à mettre à jour et sélectionnez **Propriétés**.  
  
6.  Dans la boîte de dialogue **Propriétés des statistiques –***nom_statistiques*, cochez la case **Mettre à jour les statistiques pour ces colonnes**, puis cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-update-a-specific-statistics-object"></a>Pour mettre à jour un objet de statistiques spécifique  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- The following example updates the statistics for the AK_SalesOrderDetail_rowguid index of the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail AK_SalesOrderDetail_rowguid;   
    GO  
    ```  
  
#### <a name="to-update-all-statistics-in-a-table"></a>Pour mettre à jour toutes les statistiques d'une table  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all indexes on the SalesOrderDetail table.   
    UPDATE STATISTICS Sales.SalesOrderDetail;   
    GO  
    ```  
  
 Pour plus d’informations, consultez [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).  
  
#### <a name="to-update-all-statistics-in-a-database"></a>Pour mettre à jour toutes les statistiques d'une base de données  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- The following example updates the statistics for all tables in the database.   
    EXEC sp_updatestats;  
    ```  
  
 Pour plus d’informations, consultez [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).  
  
  
