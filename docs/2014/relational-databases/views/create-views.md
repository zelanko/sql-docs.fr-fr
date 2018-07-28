---
title: Créer des vues | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], creating
ms.assetid: 0b7bd2a1-544c-42ba-8e7b-4822f34d7b64
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9cd129fda0f6331c0873700be81f4fdc982deeac
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37248309"
---
# <a name="create-views"></a>Créer des vues
  Vous pouvez créer des vues dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Une vue peut être utilisée aux fins suivantes :  
  
-   pour affiner, simplifier et personnaliser la perception de la base de données par chaque utilisateur ;  
  
-   comme mécanisme de sécurité en permettant aux utilisateurs d'accéder aux données par le biais de la vue, sans leur accorder d'autorisations qui leur permettraient d'accéder directement aux tables de base sous-jacentes de la vue ;  
  
-   pour fournir une interface à compatibilité descendante pour émuler une table dont le schéma a été modifié.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer une vue, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Vous ne pouvez créer des vues que dans la base de données actuelle.  
  
 Une vue ne peut faire référence qu'à un maximum de 1 024 colonnes.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'autorisation CREATE VIEW dans la base de données et l'autorisation ALTER sur le schéma dans lequel la vue est créée.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-view-by-using-the-query-and-view-designer"></a>Pour créer une vue à l'aide du Concepteur de requêtes et de vues  
  
1.  Dans l' **Explorateur d'objets**, développez la base de données dans laquelle vous souhaitez créer votre nouvelle vue.  
  
2.  Cliquez avec le bouton droit sur le dossier **Vues** , puis cliquez sur **Nouvelle vue**.  
  
3.  Dans la boîte de dialogue **Ajouter une table** , sélectionnez le ou les éléments que vous souhaitez inclure dans votre nouvelle vue dans l'un des onglets suivants : Tables, Vues, Fonctions et Synonymes.  
  
4.  Cliquez sur **Ajouter**, puis sur **Fermer**.  
  
5.  Dans le **volet Schéma**, sélectionnez les colonnes ou d'autres éléments à inclure dans la nouvelle vue.  
  
6.  Dans le **volet Critères**, sélectionnez les critères de tri ou de filtre supplémentaires pour les colonnes.  
  
7.  Dans le menu **Fichier**, cliquez sur **Enregistrer***nom_vue*.  
  
8.  Dans la boîte de dialogue **Choisir un nom** , entrez un nom pour la nouvelle vue et cliquez sur **OK**.  
  
     Pour plus d’informations sur le Concepteur de requêtes et de vues, consultez [Outils du concepteur de requêtes et de vues &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-view"></a>Pour créer une vue  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
    GO  
    -- Query the view  
    SELECT FirstName, LastName, HireDate  
    FROM HumanResources.EmployeeHireDate  
    ORDER BY LastName;  
  
    ```  
  
 Pour plus d’informations, consultez [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).  
  
  