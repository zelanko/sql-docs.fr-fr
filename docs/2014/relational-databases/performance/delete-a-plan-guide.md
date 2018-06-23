---
title: Supprimer un repère de plan | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-plan-guides
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- plan guides [SQL Server], deleting
ms.assetid: aa4d3188-6927-43de-a3e3-90fc16eeaca7
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2c67e2a1d5ff2f70bfc603335cee9c0733105f85
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139789"
---
# <a name="delete-a-plan-guide"></a>Supprimer un repère de plan
  Vous pouvez supprimer (éliminer) un repère de plan dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Avec [!INCLUDE[tsql](../../includes/tsql-md.md)], vous pouvez également supprimer tous les repères de plan dans une base de données.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer un repère de plan, à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 La suppression d'un repère de plan OBJECT nécessite l'autorisation ALTER sur l'objet (par exemple : fonction, procédure stockée) qui est référencé par le repère de plan. Tous les autres repères de plan nécessitent l'autorisation ALTER DATABASE.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-plan-guide"></a>Pour supprimer un repère de plan  
  
1.  Cliquez sur le signe plus pour développer la base de données dans laquelle vous souhaitez supprimer un repère de plan, puis cliquez sur le signe plus pour développer le dossier **Programmabilité** .  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Repères de plan** .  
  
3.  Cliquez avec le bouton droit sur le repère de plan à supprimer, puis sélectionnez **Supprimer**.  
  
4.  Dans la boîte de dialogue **Supprimer un objet** , assurez-vous que le repère de plan correct est sélectionné, puis cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-single-plan-guide"></a>Pour supprimer un repère de plan unique  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    --Create a procedure on which to define the plan guide.  
    IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
        DROP PROCEDURE Sales.GetSalesOrderByCountry;  
    GO  
    CREATE PROCEDURE Sales.GetSalesOrderByCountry   
        (@Country nvarchar(60))  
    AS  
    BEGIN  
        SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country;  
    END  
    GO  
    --Create the plan guide.  
    EXEC sp_create_plan_guide N'Guide3',  
        N'SELECT *  
        FROM Sales.SalesOrderHeader AS h   
        INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
        INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
        WHERE t.CountryRegionCode = @Country',  
        N'OBJECT',  
        N'Sales.GetSalesOrderByCountry',  
        NULL,  
        N'OPTION (OPTIMIZE FOR (@Country = N''US''))';  
    GO  
    --Drop the plan guide.  
    EXEC sp_control_plan_guide N'DROP', N'Guide3';  
    GO  
    ```  
  
#### <a name="to-delete-all-plan-guides-in-a-database"></a>Pour supprimer tous les repères de plan dans une base de données  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_control_plan_guide N'DROP ALL';  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql).  
  
  
