---
title: Insertion et mise à jour des données dans une table (tutoriel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- inserting and updating data
ms.assetid: 514dc87a-b829-43b5-8fc8-1a400a260284
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 19e6683baeb0a82c77a858b04f18695ba7120b15
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63250126"
---
# <a name="inserting-and-updating-data-in-a-table-tutorial"></a>Insertion et mise à jour des données dans une table (Didacticiel)
  Une fois que vous avez créé la table **Products**, vous pouvez insérer des données dans la table à l’aide de l’instruction INSERT. Une fois les données insérées, vous allez modifier le contenu d'une ligne à l'aide d'une l'instruction UPDATE. Vous allez utiliser la clause WHERE de l'instruction UPDATE pour restreindre la mise à jour à une seule ligne. Les quatre instructions entrent les données suivantes.  
  
|ProductID|ProductName|Price|ProductDescription|  
|---------------|-----------------|-----------|------------------------|  
|1|Clamp|12.48|Workbench clamp|  
|50|Screwdriver|3.17|Flat head|  
|75|Tire Bar||Outil pour changer des pneus.|  
|3000|3mm Bracket|52||  
  
 La syntaxe de base est la suivante : INSERT, nom de la table, liste de colonnes, les valeurs, puis une liste des valeurs à insérer. Les deux tirets en début de ligne indiquent que celle-ci est un commentaire et que le texte sera ignoré par le compilateur. Dans ce cas, le commentaire décrit une variation autorisée de la syntaxe.  
  
### <a name="to-insert-data-into-a-table"></a>Pour insérer des données dans une table  
  
1.  Exécutez l'instruction suivante pour insérer une ligne dans la table `Products` créée au cours de la tâche précédente. Voici la syntaxe de base :  
  
    ```  
    -- Standard syntax  
    INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
        VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
    GO  
  
    ```  
  
2.  L'instruction suivante montre comment vous pouvez modifier l'ordre dans lequel les paramètres sont fournis en alternant la position de `ProductID` et `ProductName` dans la liste des champs (entre parenthèses) et dans la liste des valeurs.  
  
    ```  
    -- Changing the order of the columns  
    INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
        VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
    GO  
  
    ```  
  
3.  L'instruction suivante montre que les noms des colonnes sont facultatifs tant que les valeurs sont répertoriées dans le bon ordre. Cette syntaxe est courante mais n'est pas recommandée car elle peut rendre votre code difficile à comprendre. `NULL` est spécifié pour la colonne `Price` car le prix du produit n’est pas encore connu.  
  
    ```  
    -- Skipping the column list, but keeping the values in order  
    INSERT dbo.Products  
        VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
    GO  
  
    ```  
  
4.  Le nom de schéma est facultatif tant que vous accédez et modifiez une table dans votre schéma par défaut. Comme la colonne `ProductDescription` autorise les valeurs Null et qu'aucune valeur n'est fournie, le nom de colonne et la valeur `ProductDescription` peuvent être supprimés de l'instruction complètement.  
  
    ```  
    -- Dropping the optional dbo and dropping the ProductDescription column  
    INSERT Products (ProductID, ProductName, Price)  
        VALUES (3000, '3mm Bracket', .52)  
    GO  
    ```  
  
### <a name="to-update-the-products-table"></a>Pour mettre à jour la table Products  
  
1.  Tapez et exécutez l'instruction `UPDATE` suivante pour remplacer le `ProductName` du deuxième produit à partir de `Screwdriver`par `Flat Head Screwdriver`.  
  
    ```  
    UPDATE dbo.Products  
        SET ProductName = 'Flat Head Screwdriver'  
        WHERE ProductID = 50  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Lecture des données dans une table &#40;Didacticiel&#41;](lesson-1-4-reading-the-data-in-a-table.md)  
  
## <a name="see-also"></a>Voir aussi  
 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)   
 [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)  
  
  
