---
title: Synthétiser ou regrouper des valeurs de toutes les lignes d’une Table (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- aggregate functions [SQL Server], summarizing query results
ms.assetid: f5af876e-f937-4110-ba09-07999c35a699
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 33d44b48571839d9695893021f6cdc1c8bb63f06
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52812801"
---
# <a name="summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools"></a>Synthétiser ou regrouper des valeurs de toutes les lignes d'une table (Visual Database Tools)
  À l'aide d'une fonction d'agrégation, vous pouvez créer une synthèse pour toutes les valeurs d'une table. Ainsi, vous pouvez, comme dans l'exemple illustré ci-dessous, créer une requête qui affiche le prix total de tous les livres de la table `titles` :  
  
```  
SELECT SUM(price)  
FROM titles  
```  
  
 Vous pouvez créer plusieurs agrégations dans la même requête en utilisant des fonctions d'agrégation avec plusieurs colonnes. Il est par exemple possible de créer une requête qui calcule le total de la colonne `price` et la moyenne de la colonne `discount`.  
  
 Vous pouvez par ailleurs agréger la même colonne de différentes façons (total, comptage et moyenne) dans la même requête. Ainsi, la requête ci-dessous établit la moyenne et totalise la colonne `price` de la table `titles` :  
  
```  
SELECT AVG(price), SUM(price)  
FROM titles  
```  
  
 Si vous ajoutez une condition de recherche, vous pouvez agréger le sous-ensemble de lignes qui répond à cette condition.  
  
> [!NOTE]  
>  Vous pouvez aussi compter toutes les lignes de la table ou celles qui répondent à une condition spécifique. Pour plus d’informations, consultez [Compter les lignes d’une table &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 Lorsque vous créez une seule valeur d'agrégation pour toutes les lignes d'une table, seules les valeurs agrégées s'affichent. Par exemple, si vous totalisez la valeur de la colonne `price` de la table `titles` , les titres individuels, les noms des éditeurs, etc. ne sont pas affichés.  
  
> [!NOTE]  
>  Si vous calculez des sous-totaux, en d’autres termes si vous créez des groupes, vous pouvez afficher des valeurs de colonne pour chaque groupe. Pour plus d’informations, consultez [Regrouper des lignes dans les résultats de requête &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).  
  
### <a name="to-aggregate-values-for-all-rows"></a>Pour agréger les valeurs de toutes les lignes  
  
1.  Assurez-vous que la table à agréger figure déjà dans le volet Schéma.  
  
2.  Cliquez avec le bouton droit sur un point de l’arrière-plan du volet Schéma, puis choisissez **Grouper par** dans le menu contextuel. Le [Concepteur de requêtes et de vues](query-and-view-designer-tools-visual-database-tools.md) ajoute une colonne **Group By** à la grille dans le volet Critères.  
  
3.  Ajoutez la colonne à agréger dans le volet Critères. Assurez-vous que la colonne est marquée pour la sortie.  
  
     Le Concepteur de requêtes et de vues assigne automatiquement un alias de colonne à la colonne que vous agrégez. Il est possible de remplacer cet alias par un autre plus significatif. Pour plus d’informations, consultez [Créer des alias de colonnes &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).  
  
4.  Dans le **Group By** colonne de la grille, sélectionnez l’approprié fonction d’agrégation, telles que : **Somme**, **Avg**, **Min**, **Max**, **nombre**. Pour n’agréger que des lignes uniques dans le jeu de résultats, choisissez une fonction d’agrégation avec l’option DISTINCT, telle que **Min Distinct**. Évitez des options comme **Group By**, **Expression**ou **Where**, car ces options ne s’appliquent pas quand vous agrégez toutes les lignes.  
  
     Le Concepteur de requêtes et de vues remplace le nom de colonne dans l’instruction figurant dans le [volet SQL](sql-pane-visual-database-tools.md) par le nom de la fonction d’agrégation que vous spécifiez. Par exemple, l'instruction SQL peut se présenter de la manière suivante :  
  
    ```  
    SELECT SUM(price)  
    FROM titles  
    ```  
  
5.  Si vous souhaitez créer plusieurs agrégations dans la requête, répétez les étapes 3 et 4.  
  
     Quand vous ajoutez une autre colonne à la liste de résultats de la requête ou à la liste Order by, le Concepteur de requêtes et de vues ajoute automatiquement le terme **Group By** dans la colonne **Group By** de la grille. Sélectionnez la fonction d'agrégation appropriée.  
  
6.  Ajoutez des conditions de recherche, le cas échéant, afin de spécifier les sous-ensembles de lignes que vous voulez synthétiser.  
  
 Quand vous exécutez la requête, le volet Résultats affiche les agrégations que vous avez définies.  
  
> [!NOTE]  
>  Le Concepteur de requêtes et de vues conserve les fonctions d'agrégation dans l'instruction SQL du volet SQL jusqu'à ce que vous désactiviez explicitement le mode Grouper par. Par conséquent, si vous modifiez votre requête en changeant son type, les tables ou autres objets table présents dans le volet Schéma, la requête obtenue peut comporter des fonctions d'agrégation non valides.  
  
## <a name="see-also"></a>Voir aussi  
 [Trier et grouper les résultats de requête &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Résumer les résultats de la requête &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)  
  
  
