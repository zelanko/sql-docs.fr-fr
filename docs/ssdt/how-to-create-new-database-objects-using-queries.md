---
title: "Procédure : créer de nouveaux objets de base de données à l'aide de requêtes | Microsoft Docs"
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac983ac7-f9c4-495d-8a99-e1ba370fb271
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 67eca663682469b9d98cc88486da76d78fe8890e
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094217"
---
# <a name="how-to-create-new-database-objects-using-queries"></a>Procédure : créer de nouveaux objets de base de données à l'aide de requêtes
Si vous préférez utiliser des scripts pour créer ou modifier des affichages, des procédures stockées, des fonctions, des déclencheurs ou des types définis par l'utilisateur, vous pouvez utiliser l'Éditeur Transact\-SQL. L'Éditeur Transact\-SQL offre la prise en charge d'IntelliSense et d'autres langages. Pour plus d’informations, consultez [Utiliser l'Éditeur Transact-SQL pour modifier et exécuter des scripts](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md).  
  
L'Éditeur Transact\-SQL est appelé lorsque vous utilisez le menu contextuel **Afficher le code** pour ouvrir une entité de base de données dans une base de données connectée ou un projet. Il s'ouvre aussi automatiquement lorsque vous utilisez le menu contextuel **Nouvelle requête** de l'Explorateur d'objets SQL Server, ou lorsque vous ajoutez un nouvel objet de script à un projet de base de données. Si vous n'êtes pas connecté à une base de données, mais que vous souhaitez exécuter une requête par rapport à une base de données, vous pouvez aussi utiliser la boîte de dialogue **Nouvelle connexion à la requête** en sélectionnant le menu **Éditeur Transact-SQL** du menu **SQL** pour vous connecter à une base de données et démarrer l'Éditeur Transact\-SQL.  
  
> [!WARNING]  
> Les procédures suivantes utilisent les entités créées dans les procédures précédentes de la section [Développement d’une base de données connectée](../ssdt/connected-database-development.md).  
  
### <a name="to-create-a-new-table-using-a-transact-sql-query"></a>Pour créer une nouvelle table à l'aide d'une requête Transact\-SQL  
  
1.  Cliquez avec le bouton droit sur le nœud de base de données **Trade** et sélectionnez **Nouvelle requête**.  
  
2.  Dans le volet de script, collez le code suivant :  
  
    ```  
  
    CREATE TABLE [dbo].[Fruits] (  
        [Id]         INT NOT NULL,  
        [Perishable] BIT DEFAULT ((1)) NULL,  
        PRIMARY KEY CLUSTERED ([Id] ASC),  
        FOREIGN KEY ([Id]) REFERENCES [dbo].[Products] ([Id])   
    );  
    ```  
  
3.  Cliquez sur le bouton **Exécuter la requête** dans la barre d'outil de l'Éditeur Transact\-SQL pour exécuter cette requête.  
  
4.  Dans l’**Explorateur d'objets SQL Server**, cliquez avec le bouton droit sur **Trade** et sélectionnez **Actualiser**. Vous pouvez remarquer que la table **Fruits** a été ajoutée à la base de données.  
  
### <a name="to-create-a-new-function"></a>Pour créer une nouvelle fonction  
  
1.  Remplacez le code dans l'Éditeur Transact\-SQL actuel par le code suivant :  
  
    ```  
  
    CREATE FUNCTION [dbo].GetProductsBySupplier  
    (  
    @SupplierId int  
    )  
    RETURNS @returntable TABLE   
    (  
    [Id] int NOT NULL,   
    [Name] NVARCHAR (128) NOT NULL,  
    [Shelflife] INT NOT NULL,  
    [SupplierId] INT NOT NULL,  
    [CustomerId] INT NOT NULL  
    )  
    AS  
    BEGIN  
    INSERT @returntable  
    SELECT *  from Products p  
    where p.SupplierId = @SupplierId  
    RETURN   
    END  
    ```  
  
    Cette fonction retourne toutes les lignes de la table `Products` dont le `SupplierId` correspond au paramètre spécifié. Cliquez sur le bouton **Exécuter la requête** dans la barre d'outil de l'Éditeur Transact\-SQL pour exécuter cette requête.  
  
2.  Dans l’Explorateur d'objets SQL Server, sous le nœud **Trade**, développez les nœuds **Programmabilité** et **Fonctions**. Vous trouverez la fonction que vous venez de créer sous **Fonctions table**.  
  
### <a name="to-create-a-new-view"></a>Pour créer un nouvel affichage  
  
1.  Remplacez le code dans l'Éditeur Transact\-SQL actuel par le code suivant. Cliquez ensuite sur le bouton **Exécuter la requête** situé au-dessus de l'éditeur pour exécuter cette requête.  
  
    ```  
    CREATE VIEW [dbo].PerishableFruits   
    AS SELECT p.Id, p.Name FROM dbo.Products p  
    join dbo.Fruits f on f.Id = p.Id  
    where f.Perishable = 1  
    ```  
  
2.  Dans l'Explorateur d'objets SQL Server, sous le nœud **Trade**, développez le nœud **Affichage** pour rechercher l'affichage que vous venez de créer.  
  
## <a name="see-also"></a> Voir aussi  
[Gérer des tables et des relations, et résoudre les erreurs](../ssdt/manage-tables-relationships-and-fix-errors.md)  
[Utiliser l'Éditeur Transact-SQL pour modifier et exécuter des scripts](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md)  
  
