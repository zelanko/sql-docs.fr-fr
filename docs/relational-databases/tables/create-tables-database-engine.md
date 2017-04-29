---
title: "Créer des tables (moteur de base de données) | Microsoft Docs"
ms.custom: 
ms.date: 09/22/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- table creation [SQL Server], Visual Database Tools
ms.assetid: 6f7c6ac5-e6d3-4dca-831e-b28442ba535b
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 57e54a247e190cdf6e52746ca591af5cc4de8507
ms.lasthandoff: 04/11/2017

---
# <a name="create-tables-database-engine"></a>Créer des tables (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Vous pouvez créer une table, la nommer et l'ajouter à une base de données existante dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> **REMARQUE :** Si vous êtes connecté à une base de données SQL Azure, la nouvelle option de table lance un script de création de modèle de table. Modifiez les paramètres, puis exécutez le script pour créer une table. Pour plus d'informations, consultez [SQL Azure Overview (en anglais)](http://go.microsoft.com/fwlink/?LinkId=163948).  
   
 
  
##  <a name="Permissions"></a> Vérifiez d’abord les autorisations dont vous bénéficiez.  
Cette tâche nécessite une autorisation CREATE TABLE dans la base de données et une autorisation ALTER pour le schéma dans lequel la table est créée.  
  
 Si des colonnes dans l’instruction CREATE TABLE sont définies comme type CLR défini par l’utilisateur, la propriété du type ou une autorisation REFERENCES sont nécessaires.  
  
 Si des colonnes dans l'instruction CREATE TABLE sont associées à une collection de schémas XML, la propriété de la collection de schémas XML ou une autorisation REFERENCES pour le type est nécessaire.  
  
 
## <a name="using-table-designer"></a>Utilisation du Concepteur de tables  
  
1.  Dans SSMS, dans **l’Explorateur d’objets**, connectez-vous à l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui contient la base de données à modifier.  
  
2.  Dans l' **Explorateur d'objets**, développez le nœud **Bases de données** , puis la base de données qui va contenir la nouvelle table.  
  
3.  Cliquez avec le bouton droit sur le nœud **Tables** de votre base de données dans l’Explorateur d’objets, puis cliquez sur **Nouvelle table**.  
  
4.  Tapez les noms des colonnes, choisissez des types de données et spécifiez si les valeurs null sont autorisées pour chaque colonne, comme indiqué dans l'illustration suivante.  
  
     ![AddColumnsinTableDesigner](../../relational-databases/tables/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")  
  
5.  Pour spécifier davantage de propriétés pour une colonne, par exemple des valeurs d'identité ou de colonne calculée, cliquez sur la colonne et choisissez les propriétés appropriées dans l'onglet des propriétés de la colonne. Pour plus d’informations sur les propriétés des colonnes, consultez [Propriétés des colonnes de table &#40;SQL Server Management Studio&#41;](../../relational-databases/tables/table-column-properties-sql-server-management-studio.md).  
  
6.  Pour spécifier une colonne comme clé primaire, cliquez avec le bouton droit sur la colonne et sélectionnez **Définir la clé primaire**. Pour plus d’informations, consultez [Create Primary Keys](../../relational-databases/tables/create-primary-keys.md).  
  
7.  Pour créer des relations de clé étrangère, des contraintes de validation ou des index, cliquez avec le bouton droit dans le volet Concepteur de tables et sélectionnez un objet dans la liste, comme indiqué dans l'illustration suivante.  
  
     ![AddTableObjects](../../relational-databases/tables/media/addtableobjects.gif "AddTableObjects")  
  
     Pour plus d'informations sur ces objets, consultez [Create Foreign Key Relationships](../../relational-databases/tables/create-foreign-key-relationships.md), [Create Check Constraints](../../relational-databases/tables/create-check-constraints.md) et [Indexes](../../relational-databases/indexes/indexes.md).  
  
8.  Par défaut, la table est contenue dans le schéma **dbo** . Pour spécifier un schéma différent pour la table, cliquez avec le bouton droit dans le volet Concepteur de tables et sélectionnez **Propriétés** , comme indiqué dans l’illustration suivante. Dans la liste déroulante **Schémas** , sélectionnez le schéma approprié.  
  
     ![Specifyatableschema](../../relational-databases/tables/media/specifyatableschema.gif "Specifyatableschema")  
  
     Pour plus d'informations sur les schémas, consultez [Create a Database Schema](../../relational-databases/security/authentication-access/create-a-database-schema.md).  
  
9. Dans le menu **Fichier** , choisissez **Enregistrer** *nom de la table*.  
  
10. Dans la boîte de dialogue **Choisir un nom** , tapez un nom pour la table et cliquez sur **OK**.  
  
11. Pour afficher la nouvelle table, dans l' **Explorateur d'objets**, développez le nœud **Tables** et appuyez sur la touche **F5** pour actualiser la liste d'objets. La nouvelle table s'affiche dans la liste des tables.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
## <a name="using-query-editor"></a>Utilisation de l’Éditeur de requête  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    CREATE TABLE dbo.PurchaseOrderDetail  
    (  
        PurchaseOrderID int NOT NULL  
        ,LineNumber smallint NOT NULL  
        ,ProductID int NULL  
        ,UnitPrice money NULL  
        ,OrderQty smallint NULL  
        ,ReceivedQty float NULL  
        ,RejectedQty float NULL  
        ,DueDate datetime NULL  
    );  
    ```  
  
 Pour obtenir d’autres exemples, consultez [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
  

