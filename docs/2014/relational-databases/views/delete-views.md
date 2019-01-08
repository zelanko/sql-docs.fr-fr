---
title: Supprimer des vues | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- dropping views
- deleting views
- views [SQL Server], deleting
- removing views
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b7e727451fb0f9dc7a3d0726a2cb0fa2d6adf997
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52513491"
---
# <a name="delete-views"></a>Supprimer des vues
  Vous pouvez supprimer (ignorer) des vues dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  

  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Lorsque vous supprimez une vue, sa définition et d'autres informations la concernant sont supprimées du catalogue système. Toutes les autorisations pour la vue sont également supprimées.  
  
-   Toute vue d'une table qui est supprimée au moyen de `DROP TABLE` doit être supprimée de manière explicite à l'aide de `DROP VIEW`.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite soit une autorisation ALTER sur SCHEMA, soit une autorisation CONTROL sur OBJECT.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-view-from-a-database"></a>Pour supprimer une vue d'une base de données  
  
1.  Dans l' **Explorateur d'objets**, développez la base de données qui contient la vue que vous souhaitez supprimer, puis le dossier **Vues** .  
  
2.  Cliquez avec le bouton droit sur la vue à supprimer, puis cliquez sur **Supprimer**.  
  
3.  Dans la boîte de dialogue **Supprimer l'objet** , cliquez sur **OK**.  
  
    > [!IMPORTANT]  
    >  Cliquez sur **Afficher les dépendances** dans la boîte de dialogue **Supprimer un objet** pour ouvrir la boîte de dialogue _Dépendances de_ **nom_vue**. Cette opération affiche tous les objets qui dépendent de la vue et tous les objets dont la vue dépend.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-view-from-a-database"></a>Pour supprimer une vue d'une base de données  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple supprime la vue spécifiée uniquement si cette vue existe déjà.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    IF OBJECT_ID ('HumanResources.EmployeeHireDate', 'V') IS NOT NULL  
    DROP VIEW HumanResources.EmployeeHireDate;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).  
  
  
