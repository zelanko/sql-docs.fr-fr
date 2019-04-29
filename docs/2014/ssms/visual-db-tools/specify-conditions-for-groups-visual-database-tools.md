---
title: Spécifier des conditions pour des groupes (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query groups
- group query conditions [SQL Server]
ms.assetid: 269ad9c5-3261-4526-badf-7be3c869f229
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bc0f9319e4d598548111b44b1a10542773a7daa4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63049143"
---
# <a name="specify-conditions-for-groups-visual-database-tools"></a>Spécifier des conditions pour des groupes (Visual Database Tools)
  Vous pouvez limiter les groupes qui apparaissent dans une requête en spécifiant une condition qui s’applique à l’ensemble des groupes (une clause HAVING). Après regroupement et agrégation des données, les conditions de la clause HAVING sont appliquées. Seuls les groupes qui répondent aux conditions apparaissent dans la requête.  
  
 Supposons que vous vouliez voir le prix moyen de tous les livres pour chaque éditeur dans une table `titles` , mais uniquement dans le cas où ce prix serait supérieur à 10 $. Dans ce cas, vous pouvez spécifier une clause HAVING avec une condition telle que `AVG(price) > 10`.  
  
> [!NOTE]  
>  Il peut arriver parfois que vous souhaitiez exclure des lignes individuelles de groupes avant d'appliquer une condition aux groupes dans leur ensemble. Pour plus d’informations, consultez [Utiliser les clauses HAVING et WHERE dans la même requête &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 Vous pouvez créer des conditions complexes pour une clause HAVING en utilisant AND et OR pour lier les conditions. Pour plus d’informations sur l’utilisation de AND et OU dans les conditions de recherche, consultez [Spécifier plusieurs conditions de recherche pour une colonne &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md).  
  
### <a name="to-specify-a-condition-for-a-group"></a>Pour spécifier une condition destinée à un groupe  
  
1.  Spécifiez les groupes de votre requête. Pour plus d’informations, consultez [Regrouper des lignes dans les résultats de requête &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).  
  
2.  Si elle ne figure pas encore dans le [volet Critères](criteria-pane-visual-database-tools.md), ajoutez la colonne sur laquelle vous souhaitez baser la condition. (Souvent, la condition concerne une colonne qui est déjà une colonne de groupe ou de synthèse.) Vous ne pouvez pas utiliser une colonne qui ne fait pas partie d'une fonction d'agrégation ou de la clause GROUP BY.  
  
3.  Dans la colonne **Filtre**, spécifiez la condition à appliquer au groupe.  
  
     Le [Concepteur de requêtes et de vues](query-and-view-designer-tools-visual-database-tools.md) crée automatiquement une clause HAVING dans l’instruction du [volet SQL](sql-pane-visual-database-tools.md), comme illustré dans l’exemple suivant :  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
  
    ```  
  
4.  Répétez les étapes 2 et 3 pour chaque condition supplémentaire que vous souhaitez spécifier.  
  
## <a name="see-also"></a>Voir aussi  
 [Trier et regrouper des résultats de requête &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)  
  
  
