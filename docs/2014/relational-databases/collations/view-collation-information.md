---
title: Afficher des informations de classement | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], view
ms.assetid: 1338b4ea-7142-44bc-a3b9-44e54431405f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9cb0f104d1555b18d18df38027c240a392d2ac66
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918700"
---
# <a name="view-collation-information"></a>Afficher des informations de classement
    
##  <a name="Top"></a> Vous pouvez afficher le classement d'un serveur, d'une base de données ou d'une colonne dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] à l'aide des options de menu de l'Explorateur d'objets ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
##  <a name="Procedures"></a> Comment afficher un paramètre de classement  
 Vous pouvez utiliser l'un des éléments suivants :  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour afficher un paramètre de classement pour un serveur (instance de SQL Server) dans l'Explorateur d'objets**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Cliquez avec le bouton droit sur l’instance et sélectionnez **Propriétés**.  
  
 **Pour afficher un paramètre de classement pour une base de données dans l'Explorateur d'objets**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, cliquez avec le bouton droit sur la base de données et sélectionnez **Propriétés**.  
  
 **Pour afficher un paramètre de classement pour une colonne dans l'Explorateur d'objets**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, la base de données, puis **Tables**.  
  
3.  Développez la table contenant la colonne, puis développez **Colonnes**.  
  
4.  Cliquez avec le bouton droit sur la colonne et sélectionnez **Propriétés**. Si la propriété de classement est vide, la colonne n'est pas un type de données character.  
  
###  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour afficher le paramètre de classement d'un serveur**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et, dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
2.  Dans la fenêtre de requête, entrez l'instruction suivante qui utilise la fonction système SERVERPROPERTY.  
  
    ```  
    SELECT CONVERT (varchar, SERVERPROPERTY('collation'));  
    ```  
  
3.  Vous pouvez également utiliser la procédure stockée système sp_helpsort.  
  
    ```  
    EXECUTE sp_helpsort;  
    ```  
  
 **Pour afficher tous les classements pris en charge par [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et, dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
2.  Dans la fenêtre de requête, entrez l'instruction suivante qui utilise la fonction système SERVERPROPERTY.  
  
    ```  
    SELECT name, description FROM sys.fn_helpcollations();  
    ```  
  
 **Pour afficher le paramètre de classement d'une base de données**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et, dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
2.  Dans la fenêtre de requête, entrez l'instruction suivante qui utilise l'affichage catalogue système sys.databases.  
  
    ```  
    SELECT name, collation_name FROM sys.databases;  
    ```  
  
3.  Vous pouvez également utiliser la fonction système DATABASEPROPERTYEX.  
  
    ```  
    SELECT CONVERT (varchar, DATABASEPROPERTYEX('database_name','collation'));  
    ```  
  
 **Pour afficher le paramètre de classement d'une colonne**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et, dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
2.  Dans la fenêtre de requête, entrez l'instruction suivante qui utilise l'affichage catalogue système sys.columns.  
  
    ```  
    SELECT name, collation_name FROM sys.columns WHERE name = N'<insert character data type column name>';  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [sys.columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)   
 [Priorité de classement &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql)   
 [sp_helpsort &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsort-transact-sql)  
  
  
