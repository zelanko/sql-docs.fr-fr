---
title: Trier avec ORDER BY (Visual Database Tools) | Microsoft Docs
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
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 01bb085d1946c5e6ac407c6baa8a9049892bc4df
ms.lasthandoff: 04/11/2017

---
# <a name="sort-with-order-by-visual-database-tools"></a>Trier avec ORDER BY (Visual Database Tools)
Vous pouvez trier les résultats d'une requête sur la base d'une ou plusieurs colonnes des lignes retournées à l'aide d'une clause ORDER BY. Vous pouvez définir une clause ORDER BY en choisissant des options dans le volet Critères.  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a>Pour trier une requête à l'aide d'une clause ORDER BY  
  
1.  Ouvrez une requête ou créez-en une nouvelle.  
  
2.  Dans le [volet Critères](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md), cliquez sur la colonne **Type de tri** pour la ligne correspondant à la colonne que vous souhaitez utiliser pour trier les résultats de votre requête.  
  
3.  Choisissez *Croissant* ou *Décroissant* dans la liste déroulante.  
  
> [!NOTE]  
> Si vous désactivez l’entrée **Type de tri** d’une colonne, celle-ci est supprimée de la clause ORDER BY.  
  
Remarquez qu'au fur et à mesure que vous travaillez dans le volet Critères, la clause UNION de votre requête se modifie pour correspondre à vos actions les plus récentes.  
  
> [!NOTE]  
> Quand vous triez des résultats par plusieurs colonnes, spécifiez l’ordre dans lequel la recherche doit être effectuée à l’aide de la colonne **Ordre de tri** . Pour plus d’informations, consultez **Procédure : tri de plusieurs colonnes dans des requêtes**.  
  
## <a name="see-also"></a>Voir aussi  
[Trier et regrouper des résultats de requête &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Résumer les résultats de la requête &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Rubriques de procédures relatives à la conception de requêtes et de vues &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  

