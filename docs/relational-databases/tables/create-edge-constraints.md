---
title: Créer des contraintes d’arête | Microsoft Docs
ms.custom: ''
ms.date: 09/11/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 160de04e9b8fbe83e8a771f5622f4f6103a8c7bb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845597"
---
# <a name="create-edge-constraints"></a>Créer des contraintes d’arête
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

   Vous pouvez définir une contrainte d’arête dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]. 
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Une contrainte d’arête peut être définie sur une table d’arêtes de graphe uniquement. 
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  

### <a name="to-create-an-edge-constraint-on-a-new-edge-table"></a>Pour créer une contrainte d’arête sur une nouvelle table d’arêtes
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple crée une contrainte d’arête sur une table d’arêtes **bought**.  
  
 ```sql
 USE TEMPDB
 GO
 -- CREATE node and edge tables
 CREATE TABLE Customer
    (
        ID INTEGER PRIMARY KEY, 
        CustomerName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Product 
  (
        ID INTEGER PRIMARY KEY, 
        ProductName VARCHAR(100)
  ) AS NODE
 GO

 CREATE TABLE bought
    (
        PurchaseCount INT,
        CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product)
    )
 AS EDGE
 GO
 ```  

### <a name="to-add-edge-constraint-to-an-existing-edge-table"></a>Pour ajouter une contrainte d’arête à une table d’arêtes existante 
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise ALTER TABLE pour ajouter une contrainte d’arête à la table d’arêtes **bought**.
  
 ```sql
 USE TEMPDB
 GO
 -- CREATE node and edge tables
 CREATE TABLE Customer
    (
        ID INTEGER PRIMARY KEY, 
        CustomerName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Product 
  (
        ID INTEGER PRIMARY KEY, 
        ProductName VARCHAR(100)
  ) AS NODE
 GO

 CREATE TABLE bought
    (
        PurchaseCount INT
    )
 AS EDGE
 GO

 ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT1 CONNECTION (Customer TO Product)
 GO
 ```  

### <a name="creating-a-new-edge-constraint-on-existing-edge-table-with-additional-edge-constraint-clauses"></a>Création d’une nouvelle contrainte d’arête sur une table d’arêtes existante, avec des clauses de contrainte d’arête supplémentaires.
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise ALTER TABLE pour ajouter une nouvelle contrainte d’arête avec des clauses de contrainte d’arête supplémentaires sur la table d’arêtes **bought**.
  
 ```sql
 USE TEMPDB
 GO
 -- CREATE node and edge tables
 CREATE TABLE Customer
    (
        ID INTEGER PRIMARY KEY, 
        CustomerName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Supplier
    (
        ID INTEGER PRIMARY KEY, 
        SupplierName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Product 
  (
        ID INTEGER PRIMARY KEY, 
        ProductName VARCHAR(100)
  ) AS NODE
 GO

 CREATE TABLE bought
    (
        PurchaseCount INT,
        CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product)
    )
 AS EDGE
 GO

 -- Drop the existing edge constraint first and then create a new one.
 ALTER TABLE bought DROP CONSTRAINT EC_BOUGHT
 GO

 -- User ALTER TABLE to create a new edge constraint.
 ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT1 CONNECTION (Customer TO Product, Supplier TO Product)
 GO
 ```  
 Notez qu’il existe deux clauses de contrainte d’arête dans la contrainte *EC_BOUGHT1*, une qui connecte **Customer** à **Product** et l’autre qui connecte **Supplier** à **Product**. Ces deux clauses sont appliquées en disjonction. Autrement dit, une arête donnée doit satisfaire une de ces deux clauses pour être autorisée dans la table d’arêtes. 



### <a name="creating-a-new-edge-constraint-on-existing-edge-table-with-new-edge-constraint-clause"></a>Création d’une nouvelle contrainte d’arête sur une table d’arêtes existante, avec une nouvelle clause de contrainte d’arête.
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise ALTER TABLE pour ajouter une nouvelle contrainte d’arête avec une nouvelle clause de contrainte d’arête sur la table d’arêtes **bought**.
  
 ```sql
 USE TEMPDB
 GO
 -- CREATE node and edge tables
 CREATE TABLE Customer
    (
        ID INTEGER PRIMARY KEY, 
        CustomerName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Supplier
    (
        ID INTEGER PRIMARY KEY, 
        SupplierName VARCHAR(100)
    )
 AS NODE
 GO

 CREATE TABLE Product 
  (
        ID INTEGER PRIMARY KEY, 
        ProductName VARCHAR(100)
  ) AS NODE
 GO

 CREATE TABLE bought
    (
        PurchaseCount INT,
        CONSTRAINT EC_BOUGHT CONNECTION (Customer TO Product)
    )
 AS EDGE
 GO

 ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT1 CONNECTION (Supplier TO Product)
 GO
 ```  

 Dans cet exemple, nous avons créé deux contraintes d’arête distinctes sur la table d’arêtes **bought**, *EC_BOUGHT* et *EC_BOUGHT1*. Ces deux contraintes d’arête ont des clauses de contrainte d’arête différentes. Si une table d’arêtes fait l’objet de plusieurs contraintes d’arête, une arête donnée doit satisfaire **TOUTES** les contraintes d’arête pour être autorisée dans la table d’arêtes. Dans la mesure où aucune arête ne peut satisfaire à la fois *EC_BOUGHT* et *EC_BOUGHT1* ici, la table d’arêtes **bought** doit rester vide. 

 Pour que les insertions réussissent dans cette table d’arêtes, l’une des contraintes d’arête doit être supprimée, ou les deux doivent être supprimées et une nouvelle contrainte d’arête doit être créée, contenant les deux clauses de contrainte d’arête. 

 ```sql
 USE TEMPDB
 GO
 -- Drop the existing edge constraint first and then create a new one.
 ALTER TABLE bought DROP CONSTRAINT EC_BOUGHT
 GO
 
 ALTER TABLE bought DROP CONSTRAINT EC_BOUGHT1
 GO
 
 ALTER TABLE bought ADD CONSTRAINT EC_BOUGHT_NEW CONNECTION (Customer TO Product, Supplier TO Product)
 GO
 ```  

 Maintenant, pour qu’une arête donnée soit autorisée dans l’arête **bought**, elle doit satisfaire l’une des clauses de contrainte d’arête figurant dans la contrainte *EC_BOUGHT_NEW*. Par conséquent, toute arête qui essaie de connecter des nœuds valides **Customer** à **Product** ou **Supplier** à **Product**, sera autorisée. 
