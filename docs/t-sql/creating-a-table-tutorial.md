---
title: "Cr&#233;ation d&#39;une table (Didacticiel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "création de tables"
ms.assetid: 653f2dd3-36a2-4bd5-8703-71a57d244661
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Cr&#233;ation d&#39;une table (Didacticiel)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

Pour créer une table, vous devez fournir un nom pour la table et les noms et les types de données de chaque colonne dans la table. Il est aussi recommandé d'indiquer si les valeurs Null sont autorisées dans chaque colonne. Pour créer une table, vous devez avoir les autorisations `CREATE TABLE` et `ALTER SCHEMA` sur le schéma qui contiendra la table. Le rôle fixe de base de données `db_ddladmin` dispose de ces autorisations.  
  
La plupart des tables possèdent une clé primaire constituée d'une ou plusieurs colonnes de la table. Une clé primaire est toujours unique. Le [!INCLUDE[ssDE](../includes/ssde-md.md)] applique la restriction qui veut que les valeurs de clé primaire ne peuvent pas être répétées dans la table.  
  
Pour obtenir une liste des types de données et des liens contenant une description individuelle, consultez [Types de données &#40;Transact-SQL&#41;](../t-sql/data-types/data-types-transact-sql.md).  
  
> [!NOTE]  
> Vous pouvez configurer le [!INCLUDE[ssDE](../includes/ssde-md.md)] pour qu’il respecte la casse ou non. Si vous installez le [!INCLUDE[ssDE](../includes/ssde-md.md)] pour qu’il respecte la casse, les noms des objets doivent toujours avoir la même casse. Par exemple, une table nommée OrderData est différente d'une table nommée ORDERDATA. Si le [!INCLUDE[ssDE](../includes/ssde-md.md)] ne respecte pas la casse, ces deux noms de tables sont considérés comme une seule et même table, et ce nom ne peut être utilisé qu’une fois.  
  
### Pour créer une base de données qui contient la nouvelle table  
  
-   Entrez le code suivant dans une fenêtre de l'Éditeur de requête.  
  
    ```  
    USE master;  
    GO  
  
    --Delete the TestData database if it exists.  
    IF EXISTS(SELECT * from sys.databases WHERE name='TestData')  
    BEGIN  
        DROP DATABASE TestData;  
    END  
  
    --Create a new database called TestData.  
    CREATE DATABASE TestData;  
    Press the F5 key to execute the code and create the database.  
    ```  
  
### Passer la connexion de l'Éditeur de requête à la base de données TestData  
  
-   Dans une fenêtre Éditeur de requêtes, tapez et exécutez le code suivant pour modifier votre connexion à la base de données `TestData`.  
  
    ```  
    USE TestData  
    GO  
    ```  
  
### Pour créer une table  
  
-   Dans une fenêtre Éditeur de requêtes, tapez et exécutez le code suivant pour créer une simple table nommée `Products`. Les colonnes de la table sont nommées `ProductID`, `ProductName`, `Price`, et `ProductDescription`. La colonne `ProductID` est la clé primaire de la table. `int`, `varchar(25)`, `money` et `text` sont tous des types de données. Seules les colonnes `Price` et `ProductionDescription` peuvent n'avoir aucune données lors de l'insertion ou de la modification d'une ligne. Cette instruction contient un élément facultatif (`dbo.`) appelé un schéma. Le schéma est l'objet de base de données qui est propriétaire de la table. Si vous êtes administrateur, `dbo` est le schéma par défaut. `dbo` représente le propriétaire de la base de données.  
  
    ```  
    CREATE TABLE dbo.Products  
       (ProductID int PRIMARY KEY NOT NULL,  
        ProductName varchar(25) NOT NULL,  
        Price money NULL,  
        ProductDescription text NULL)  
    GO  
    ```  
  
## Tâche suivante de la leçon  
[Insertion et mise à jour des données dans une table &#40;Didacticiel&#41;](../t-sql/inserting-and-updating-data-in-a-table-tutorial.md)  
  
## Voir aussi  
[CREATE TABLE &#40;Transact-SQL&#41;](../t-sql/statements/create-table-transact-sql.md)  
  
  
  
