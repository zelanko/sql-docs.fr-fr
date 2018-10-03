---
title: Créer des tables (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- table creation [SQL Server], Visual Database Tools
ms.assetid: 6f7c6ac5-e6d3-4dca-831e-b28442ba535b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 411599f503b13ed5f6000963da7b25cf73260e7f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081049"
---
# <a name="create-tables-database-engine"></a>Créer des tables (moteur de base de données)
  Vous pouvez créer une table, la nommer et l'ajouter à une base de données existante dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  Si vous êtes connecté à une base de données SQL Azure, la nouvelle option de table lance un script de création de modèle de table. Modifiez les paramètres, puis exécutez le script pour créer une table. Pour plus d'informations, consultez [SQL Azure Overview (en anglais)](http://go.microsoft.com/fwlink/?LinkId=163948).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour créer une table, à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite une autorisation CREATE TABLE dans la base de données et une autorisation ALTER pour le schéma dans lequel la table a été créée.  
  
 Si des colonnes dans l'instruction CREATE TABLE sont définies comme un type de données CLR défini par l'utilisateur, la propriété du type ou une autorisation REFERENCES est nécessaire.  
  
 Si des colonnes dans l'instruction CREATE TABLE sont associées à une collection de schémas XML, la propriété de la collection de schémas XML ou une autorisation REFERENCES pour le type est nécessaire.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-table-with-table-designer"></a>Pour créer une table avec le Concepteur de tables  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui contient la base de données à modifier.  
  
2.  Dans l' **Explorateur d'objets**, développez le nœud **Bases de données** , puis la base de données qui va contenir la nouvelle table.  
  
3.  Cliquez avec le bouton droit sur le nœud **Tables** de votre base de données dans l’Explorateur d’objets, puis cliquez sur **Nouvelle table**.  
  
4.  Tapez les noms des colonnes, choisissez des types de données et spécifiez si les valeurs null sont autorisées pour chaque colonne, comme indiqué dans l'illustration suivante.  
  
     ![AddColumnsinTableDesigner](../../database-engine/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")  
  
5.  Pour spécifier davantage de propriétés pour une colonne, par exemple des valeurs d'identité ou de colonne calculée, cliquez sur la colonne et choisissez les propriétés appropriées dans l'onglet des propriétés de la colonne. Pour plus d’informations sur les propriétés des colonnes, consultez [Propriétés des colonnes de table &#40;SQL Server Management Studio&#41;](table-column-properties-sql-server-management-studio.md).  
  
6.  Pour spécifier une colonne comme clé primaire, cliquez avec le bouton droit sur la colonne et sélectionnez **Définir la clé primaire**. Pour plus d’informations, consultez [Create Primary Keys](../tables/create-primary-keys.md).  
  
7.  Pour créer des relations de clé étrangère, des contraintes de validation ou des index, cliquez avec le bouton droit dans le volet Concepteur de tables et sélectionnez un objet dans la liste, comme indiqué dans l'illustration suivante.  
  
     ![AddTableObjects](../../database-engine/media/addtableobjects.gif "AddTableObjects")  
  
     Pour plus d'informations sur ces objets, consultez [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md), [Create Check Constraints](../tables/create-check-constraints.md) et [Indexes](../indexes/indexes.md).  
  
8.  Par défaut, la table est contenue dans le schéma **dbo** . Pour spécifier un schéma différent pour la table, cliquez avec le bouton droit dans le volet Concepteur de tables et sélectionnez **Propriétés** , comme indiqué dans l’illustration suivante. Dans la liste déroulante **Schémas** , sélectionnez le schéma approprié.  
  
     ![Specifyatableschema](../../database-engine/media/specifyatableschema.gif "Specifyatableschema")  
  
     Pour plus d'informations sur les schémas, consultez [Create a Database Schema](../security/authentication-access/create-a-database-schema.md).  
  
9. Dans le menu **Fichier** , choisissez **Enregistrer** *nom de la table*.  
  
10. Dans la boîte de dialogue **Choisir un nom** , tapez un nom pour la table et cliquez sur **OK**.  
  
11. Pour afficher la nouvelle table, dans l' **Explorateur d'objets**, développez le nœud **Tables** et appuyez sur la touche **F5** pour actualiser la liste d'objets. La nouvelle table s'affiche dans la liste des tables.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-table-in-the-query-editor"></a>Pour créer une table dans l'éditeur de requête  
  
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
  
 Pour obtenir d’autres exemples, consultez [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).  
  
  
