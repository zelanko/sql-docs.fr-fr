---
title: Page filtres, boîtes de dialogue graphique (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.categorygroupproperties.filters.f1
- "10409"
- sql12.rtp.rptdesigner.seriesgroupproperties.filters.f1
- "10401"
- sql12.rtp.rptdesigner.chartproperties.filters.f1
- "10165"
ms.assetid: fab97b2f-d53f-42f2-900c-c159653d89ed
caps.latest.revision: 14
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3123a7c1ba3a520ad743ffe7dbd65dfd57443672
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317899"
---
# <a name="filters-page-chart-dialog-boxes-report-builder-and-ssrs"></a>Page Filtres, boîtes de dialogue Graphique (Générateur de rapports et SSRS)
  Cliquez sur **filtres** dans le :  
  
-   la boîte de dialogue**Propriétés du groupe de catégories** pour filtrer les points de données dans une série regroupée par catégorie ;  
  
-   la boîte de dialogue**Propriétés du graphique** pour définir les options de filtrage du graphique ;  
  
-   la boîte de dialogue**Propriétés du groupe de séries** pour limiter le nombre de séries dans le groupe sélectionné.  
  
## <a name="options"></a>Options  
 **Ajouter**  
 Cliquez pour ajouter une nouvelle clause de filtre à la liste.  
  
 **Supprimer**  
 Cliquez pour supprimer la clause de filtre sélectionnée de la liste.  
  
 **Flèche haut**  
 Cliquez pour déplacer le filtre sélectionné vers le haut de la liste.  
  
 **Flèche bas**  
 Cliquez pour déplacer le filtre sélectionné vers le bas dans la liste.  
  
 **Expression**  
 Tapez ou choisissez l'expression à laquelle vous souhaitez appliquer un filtre. Cliquez sur le bouton Expression (**fx**) pour modifier l’expression.  
  
 **Data type**  
 Sélectionnez le type de données du champ **Valeur**. Lorsque cela est possible, sélectionnez un type de données correspondant à celui du champ **Expression**.  
  
 Les valeurs dans **Expression** et **Valeur** doivent s’évaluer au même type de données. Par exemple, si **Expression** a pour valeur un champ du type de données System.Int32 et que **Valeur** a pour valeur 7, sélectionnez **Entier**dans la liste déroulante.  
  
 Si le type de données recherché ne figure pas dans la liste déroulante, écrivez une expression permettant de convertir la valeur en type de données correct. Pour plus d’informations, consultez [Exemples d’équations de filtre &#40;Générateur de rapports et SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).  
  
 **Opérateur**  
 Choisissez l'opérateur à utiliser pour comparer l'expression et la valeur.  
  
 **Value**  
 Tapez l’expression ou la valeur à comparer au contenu de l’expression dans **Expression**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupes &#40;Générateur de rapports et SSRS&#41;](report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Filtrer, regrouper et trier les données &#40;Générateur de rapports et SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
