---
title: Supprimer des vues | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-views
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dropping views
- deleting views
- views [SQL Server], deleting
- removing views
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1c869b1e4ba7cc992687baa3236c96d25b0e63e8
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="delete-views"></a>Supprimer des vues
  Vous pouvez supprimer (ignorer) des vues dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer une vue d'une base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Lorsque vous supprimez une vue, sa définition et d'autres informations la concernant sont supprimées du catalogue système. Toutes les autorisations pour la vue sont également supprimées.  
  
-   Toute vue d'une table qui est supprimée au moyen de `DROP TABLE` doit être supprimée de manière explicite à l'aide de `DROP VIEW`.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite soit une autorisation ALTER sur SCHEMA, soit une autorisation CONTROL sur OBJECT.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-view-from-a-database"></a>Pour supprimer une vue d'une base de données  
  
1.  Dans l' **Explorateur d'objets**, développez la base de données qui contient la vue que vous souhaitez supprimer, puis le dossier **Vues** .  
  
2.  Cliquez avec le bouton droit sur la vue à supprimer, puis cliquez sur **Supprimer**.  
  
3.  Dans la boîte de dialogue **Supprimer l'objet** , cliquez sur **OK**.  
  
    > [!IMPORTANT]  
    >  Cliquez sur **Afficher les dépendances** dans la boîte de dialogue **Supprimer un objet** pour ouvrir la boîte de dialogue *Dépendances de* **nom_vue**. Cette opération affiche tous les objets qui dépendent de la vue et tous les objets dont la vue dépend.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-view-from-a-database"></a>Pour supprimer une vue d'une base de données  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple supprime la vue spécifiée uniquement si cette vue existe déjà.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    IF OBJECT_ID ('HumanResources.EmployeeHireDate', 'V') IS NOT NULL  
    DROP VIEW HumanResources.EmployeeHireDate;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [DROP VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/drop-view-transact-sql.md).  
  
  
