---
title: "Créer des alias de colonnes (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bbbf69c55fcd0225583c43b3b4ae4089cc2f40ea
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="create-column-aliases-visual-database-tools"></a>Créer des alias de colonnes (Visual Database Tools)
Vous pouvez créer des alias pour les noms de colonnes, afin de faciliter l'utilisation des noms de colonnes, des calculs et des valeurs totalisées. Vous pouvez, par exemple, créer un alias de colonne pour effectuer les opérations suivantes :  
  
-   Créer un nom de colonne, tel que « Total Amount », pour une expression de type `(quantity * unit_price)` ou pour une fonction d'agrégation  
  
-   Créer un nom de colonne abrégé, tel que `"d_id"` pour `"discounts.stor_id."`  
  
Lorsque vous avez défini un alias de colonne, vous pouvez utiliser cet alias dans une requête Select pour spécifier le résultat de la requête.  
  
### <a name="to-create-a-column-alias"></a>Pour créer un alias de colonne  
  
1.  Dans le **volet Critères**, recherchez la ligne comportant la colonne de données pour laquelle vous souhaitez créer un alias et spécifiez, si nécessaire, si vous souhaitez qu’elle figure dans les résultats. Si la colonne de données ne figure pas encore dans la grille, ajoutez-la.  
  
2.  Entrez l’alias dans la colonne **Alias** de cette ligne. L'alias doit respecter les conventions d'appellation du langage SQL. Si le nom de l'alias entré comporte des espaces, le Concepteur de requêtes et de vues les entoure automatiquement à l'aide de délimiteurs.  
  
## <a name="see-also"></a>Voir aussi  
[Ajouter des colonnes à des requêtes &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md)  
[Trier et regrouper des résultats de requête &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Résumer les résultats de la requête &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Effectuer des opérations de base concernant les requêtes &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

