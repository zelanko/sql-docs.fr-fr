---
title: Créer des alias de colonne
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: c4feb18b5f01b1e999ecec5b5b8e022230912d8f
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "85977887"
---
# <a name="create-column-aliases-visual-database-tools"></a>Créer des alias de colonnes (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Vous pouvez créer des alias pour les noms de colonnes, afin de faciliter l'utilisation des noms de colonnes, des calculs et des valeurs totalisées. Vous pouvez, par exemple, créer un alias de colonne pour effectuer les opérations suivantes :  
  
-   Créer un nom de colonne, tel que « Total Amount », pour une expression de type `(quantity * unit_price)` ou pour une fonction d'agrégation  
  
-   Créer un nom de colonne abrégé, tel que `"d_id"` pour `"discounts.stor_id."`  
  
Lorsque vous avez défini un alias de colonne, vous pouvez utiliser cet alias dans une requête Select pour spécifier le résultat de la requête.  
  
### <a name="to-create-a-column-alias"></a>Pour créer un alias de colonne  
  
1.  Dans le **volet Critères**, recherchez la ligne comportant la colonne de données pour laquelle vous souhaitez créer un alias et spécifiez, si nécessaire, si vous souhaitez qu’elle figure dans les résultats. Si la colonne de données ne figure pas encore dans la grille, ajoutez-la.  
  
2.  Entrez l’alias dans la colonne **Alias** de cette ligne. L'alias doit respecter les conventions d'appellation du langage SQL. Si le nom de l'alias entré comporte des espaces, le Concepteur de requêtes et de vues les entoure automatiquement à l'aide de délimiteurs.  
  
## <a name="see-also"></a>Voir aussi  
[Ajouter des colonnes à des requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md)  
[Trier et regrouper des résultats de requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Résumer les résultats de la requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Effectuer des opérations de base concernant les requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
