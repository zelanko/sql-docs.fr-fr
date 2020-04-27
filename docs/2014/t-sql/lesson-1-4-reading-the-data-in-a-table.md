---
title: Lecture des données dans une table (tutoriel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- reading data in a table
ms.assetid: 532232c9-3d41-45cd-9150-de67a1cbfcf5
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 0649e167ebaa90267422594ccd193ba468838e6f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68187298"
---
# <a name="reading-the-data-in-a-table-tutorial"></a>Lecture des données dans une table (Didacticiel)
  Utilisez l'instruction SELECT pour lire les données dans une table. L'instruction SELECT est une des instructions [!INCLUDE[tsql](../includes/tsql-md.md)] les plus importantes et dont la syntaxe comporte beaucoup de variations. Pour ce didacticiel, vous allez travailler avec cinq versions simples.  
  
### <a name="to-read-the-data-in-a-table"></a>Pour lire les données dans une table  
  
1.  Tapez et exécutez les instructions suivantes pour lire les données dans la table `Products` .  
  
    ```  
    -- The basic syntax for reading data from a single table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
    GO  
  
    ```  
  
2.  Vous pouvez utiliser un astérisque pour sélectionner toutes les colonnes de la table. Cette opération s'utilise souvent dans les requêtes ad hoc. Vous devez fournir la liste de la colonne dans votre code permanent pour que l'instruction retourne les colonnes prédites, même si une nouvelle colonne est ajoutée à la table ultérieurement.  
  
    ```  
    -- Returns all columns in the table  
    -- Does not use the optional schema, dbo  
    SELECT * FROM Products  
    GO  
  
    ```  
  
3.  Vous pouvez omettre les colonnes que vous ne souhaitez pas retourner. Les colonnes seront retournées dans leur ordre d'apparition.  
  
    ```  
    -- Returns only two of the columns from the table  
    SELECT ProductName, Price  
        FROM dbo.Products  
    GO  
  
    ```  
  
4.  Utilisez une clause `WHERE` pour limiter les lignes retournées à l'utilisateur.  
  
    ```  
    -- Returns only two of the records in the table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
        WHERE ProductID < 60  
    GO  
  
    ```  
  
5.  Vous pouvez travailler avec les valeurs des colonnes à mesure qu'elles sont retournées. L'exemple suivant effectue une opération mathématique sur la colonne `Price` . Les colonnes ayant été modifiées de cette manière n'ont pas de nom sauf si vous en fournissez un à l'aide du mot clé `AS` .  
  
    ```  
    -- Returns ProductName and the Price including a 7% tax  
    -- Provides the name CustomerPays for the calculated column  
    SELECT ProductName, Price * 1.07 AS CustomerPays  
        FROM dbo.Products  
    GO  
    ```  
  
## <a name="functions-that-are-useful-in-a-select-statement"></a>Fonctions utiles dans une instruction SELECT  
 Pour des informations sur certaines fonctions que vous pouvez utiliser pour travailler avec des données dans les instructions SELECT, consultez les rubriques suivantes :  
  
|||  
|-|-|  
|[Fonctions de chaîne &#40;Transact-SQL&#41;](/sql/t-sql/functions/string-functions-transact-sql)|[Fonctions et types de données de date et d’heure &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|  
|[Fonctions mathématiques &#40;Transact-SQL&#41;](/sql/t-sql/functions/mathematical-functions-transact-sql)|[Fonctions texte et image &#40;Transact-SQL&#41;](/sql/t-sql/functions/text-and-image-functions-textptr-transact-sql)|  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Résumé : Création des objets de base de données](lesson-1-5-summary-creating-database-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)  
  
  
