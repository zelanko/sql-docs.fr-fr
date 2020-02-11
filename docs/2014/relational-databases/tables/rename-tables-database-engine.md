---
title: Renommer des tables (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table renaming [SQL Server]
- table names [SQL Server]
- tables [SQL Server], Visual Database Tools
- renaming tables
ms.assetid: 2f5c922d-4d71-4694-9fca-28dd99375799
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3fc62dc5f0e716273df257aba7fdc137391d3055
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68196730"
---
# <a name="rename-tables-database-engine"></a>Renommer des tables (moteur de base de données)
  Vous pouvez renommer une table dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!CAUTION]  
>  Ne renommez une table qu'après mûre réflexion. En effet, s'il existe des requêtes, des vues, des fonctions définies par l'utilisateur, des procédures stockées ou des programmes qui font référence à cette table, le changement de nom rend tous ces objets non valides.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour renommer une table à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Le fait de renommer une table ne renomme pas automatiquement les références à cette table. Vous devez modifier manuellement tout objet qui référence la table renommée. Par exemple, si vous renommez une table et si cette table est référencée dans un déclencheur, vous devez modifier le déclencheur pour refléter le nouveau nom de table. Utilisez [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) pour obtenir la liste des dépendances de la table avant de la renommer.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-rename-a-table"></a>Pour renommer une table  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur la table que vous souhaitez renommer et choisissez **Conception** dans le menu contextuel.  
  
2.  Dans le menu **Affichage** , choisissez **Propriétés**.  
  
3.  Dans le champ de la valeur **Nom** de la fenêtre **Propriétés** , tapez un nouveau nom pour la table.  
  
4.  Pour annuler cette action, appuyez sur la touche Échap avant de quitter ce champ.  
  
5.  Dans le menu **Fichier**, choisissez **Enregistrer**_nom de la table_.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-rename-a-table"></a>Pour renommer une table  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  L'exemple suivant renomme la table `SalesTerritory` en `SalesTerr` dans le schéma `Sales` . Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
    ```  
  
 Pour obtenir des exemples supplémentaires, consultez [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).  
  
  
