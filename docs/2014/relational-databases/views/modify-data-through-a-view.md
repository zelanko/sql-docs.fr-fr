---
title: Modifier les données par l’intermédiaire d’une vue | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- data modifications [SQL Server], views
- views [SQL Server], modifying data through
- modifying data [SQL Server], views
ms.assetid: 410e2812-4ebe-48b2-b95f-c7784f1c4336
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5d87430c64bac133523d7001a88a894bb3985a5f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68211675"
---
# <a name="modify-data-through-a-view"></a>Modifier les données par l'intermédiaire d'une vue
  Vous pouvez modifier les données d'une table de base sous-jacente dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour modifier des données de table via une vue, à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Consultez la section « Vues pouvant être mises à jour » dans [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite des autorisations UPDATE, INSERT ou DELETE sur la table cible, selon l'action effectuée.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-modify-table-data-through-a-view"></a>Pour modifier les données de table par le biais d'une vue  
  
1.  Dans l' **Explorateur d'objets**, développez la base de données qui contient la vue, puis développez **Vues**.  
  
2.  Cliquez avec le bouton droit sur la vue et sélectionnez **Modifier les 200 lignes du haut**.  
  
3.  Vous devrez peut-être modifier l'instruction SELECT dans le volet **SQL** pour retourner les lignes à modifier.  
  
4.  Dans le volet de **résultats** , recherchez la ligne à modifier ou à supprimer. Pour supprimer la ligne, cliquez dessus avec le bouton droit et sélectionnez **Supprimer**. Pour modifier des données dans une ou plusieurs colonnes, modifiez les données dans la colonne.  
  
    > [!IMPORTANT]  
    >  Vous ne pouvez pas supprimer une ligne si la vue référence plusieurs table de base. Vous pouvez uniquement mettre à jour les colonnes qui appartiennent à une seule table de base.  
  
5.  Pour insérer une ligne, faites défiler les lignes jusqu'à la fin et insérez les nouvelles valeurs.  
  
    > [!IMPORTANT]  
    >  Vous ne pouvez pas insérer une ligne si la vue référence plusieurs table de base.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-update-table-data-through-a-view"></a>Pour mettre à jour les données de table par le biais d'une vue  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple remplace la valeur des colonnes `StartDate` et `EndDate` d'un employé spécifique par les colonnes de référence dans la vue `HumanResources.vEmployeeDepartmentHistory`. Cette vue retourne des valeurs de deux tables. Cette instruction réussit car les colonnes qui sont modifiées proviennent uniquement d'une des tables de base.  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    UPDATE HumanResources.vEmployeeDepartmentHistory  
    SET StartDate = '20110203', EndDate = GETDATE()   
    WHERE LastName = N'Smith' AND FirstName = 'Samantha';   
    GO  
    ```  
  
 Pour plus d’informations, consultez [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql).  
  
#### <a name="to-insert-table-data-through-a-view"></a>Pour insérer des données de table par le biais d'une vue  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple insère une nouvelle ligne dans la table de base `HumanResouces.Department` en spécifiant les colonnes appropriées de la vue `HumanResources.vEmployeeDepartmentHistory`. L'instruction réussit car seules les colonnes d'une même table de base sont spécifiées et les autres colonnes de la table de base utilisent des valeurs par défaut.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    INSERT INTO HumanResources.vEmployeeDepartmentHistory (Department, GroupName)   
    VALUES ('MyDepartment', 'MyGroup');   
    GO  
    ```  
  
 Pour plus d’informations, consultez [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql).  
  
  
