---
title: Créer des extraits de code réutilisables
description: Découvrez comment créer et utiliser des extraits de code SQL Azure Data Studio, qui facilitent la création de bases de données et d’objets de base de données.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 95b0385178a5e2bd25f8b64be5f910d4f885e34b
ms.sourcegitcommit: dc8a30a4a27e15fc6671ca2674da9b7c637ec255
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88746089"
---
# <a name="create-and-use-code-snippets-to-quickly-create-transact-sql-t-sql-scripts-in-azure-data-studio"></a>Créer et utiliser des extraits de code pour créer rapidement des scripts Transact-SQL (T-SQL) dans Azure Data Studio

Les extraits de code dans Azure Data Studio sont des modèles qui facilitent la création de bases de données et d’objets de base de données. 

Azure Data Studio fournit plusieurs extraits de code T-SQL pour vous aider à générer rapidement la syntaxe appropriée. 

Des extraits de code définis par l’utilisateur peuvent également être créés.

## <a name="using-built-in-t-sql-code-snippets"></a>Utilisation d’extraits de code T-SQL intégrés

1. Pour accéder aux extraits de code disponibles, saisissez *sql* dans l’éditeur de requête pour ouvrir la liste :

   ![extraits de code](media/code-snippets/sql-snippets.png)

1. Sélectionnez l’extrait de code que vous souhaitez utiliser, et il génère le script T-SQL. Par exemple, sélectionnez *sqlCreateTable* :

   ![extraits de code de création de tables](media/code-snippets/create-table.png)

1. Mettez à jour les champs mis en surbrillance avec vos valeurs spécifiques. Par exemple, remplacez *TableName* et *Schema* par les valeurs de votre base de données :

   ![remplacer le champ de modèle](media/code-snippets/table-from-snippet.png)

   Si le champ que vous souhaitez modifier n’est plus mis en surbrillance (cela se produit lors du déplacement du curseur dans l’éditeur), cliquez avec le bouton droit sur le mot à modifier, puis sélectionnez **Modifier toutes les occurrences** :

   ![remplacer le champ de modèle](media/code-snippets/change-all.png)

1. Mettez à jour ou ajoutez tout T-SQL supplémentaire dont vous avez besoin pour l’extrait de code sélectionné. Par exemple, mettez à jour *Column1*, *Column2* et ajoutez des colonnes supplémentaires.


 
## <a name="creating-sql-code-snippets"></a>Création d’extraits de code SQL 

Vous pouvez définir vos propres extraits de code. Pour ouvrir le fichier d’extrait de code SQL en vue de le modifier :

1. Ouvrez la *Palette de commandes* (**Ctrl+Maj+P**) et saisissez *snip*, puis sélectionnez **Préférences : Ouvrir les extraits de code utilisateur** :

   ![remplacer le champ de modèle](media/code-snippets/user-snippets.png)

1. Sélectionnez **SQL** :

   > [!NOTE]
   > Azure Data Studio hérite de sa fonctionnalité d’extrait de code de Visual Studio Code, aussi cet article explique spécifiquement comment utiliser des extraits de code SQL. Pour plus d’informations, consultez [Création de vos propres extraits de code](https://code.visualstudio.com/docs/editor/userdefinedsnippets) dans la documentation de Visual Studio Code. 

   ![remplacer le champ de modèle](media/code-snippets/select-sql.png)

1. Collez le code suivant dans *sql.json* :

   ```sql
   {
   "Select top 5": {
    "prefix": "sqlSelectTop5",
    "body": "SELECT TOP 5 * FROM ${1:TableName}",
    "description": "User-defined snippet example 1"
    },
    "Create Table snippet":{
    "prefix": "sqlCreateTable2",
    "body": [
    "-- Create a new table called '${1:TableName}' in schema '${2:SchemaName}'",
    "-- Drop the table if it already exists",
    "IF OBJECT_ID('$2.$1', 'U') IS NOT NULL",
    "DROP TABLE $2.$1",
    "GO",
    "-- Create the table in the specified schema",
    "CREATE TABLE $2.$1",
    "(",
    "   $1Id INT NOT NULL PRIMARY KEY, -- primary key column",
    "   Column1 [NVARCHAR](50) NOT NULL,",
    "   Column2 [NVARCHAR](50) NOT NULL",
    "   -- specify more columns here",
    ");",
    "GO"
    ],
   "description": "User-defined snippet example 2"
   }
   }
   ```

1. Enregistrez le fichier sql.json.
1. Ouvrez une nouvelle fenêtre de l’éditeur de requête avec **Ctrl+N**.
2. Saisissez **sql** et vous verrez les deux extraits de code utilisateur que vous venez d’ajouter, *sqlCreateTable2* et *sqlSelectTop5*.

Sélectionnez un des nouveaux extraits et essayez-le !


## <a name="additional-resources"></a>Ressources supplémentaires

Pour plus d’informations sur l’éditeur SQL, consultez le [Didacticiel sur l’éditeur de code](tutorial-sql-editor.md).
