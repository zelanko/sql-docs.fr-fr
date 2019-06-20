---
title: 'Analysis Services leçon supplémentaire du didacticiel : Lignes de détails | Microsoft Docs'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: bad45d18c351e838ec944b1ae67e3ce88c7e1d20
ms.sourcegitcommit: a6949111461eda0cc9a71689f86b517de3c5d4c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263308"
---
# <a name="supplemental-lesson---detail-rows"></a>Leçon supplémentaire - Lignes de détails

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon supplémentaire, vous utilisez l’éditeur DAX pour définir une Expression de lignes de détail personnalisée. Une Expression de lignes de détail est une propriété sur une mesure, en fournissant aux utilisateurs finaux plus d’informations sur les résultats agrégés d’une mesure. 
  
Durée estimée pour effectuer cette leçon : **10 minutes**  
  
## <a name="prerequisites"></a>Prérequis  

Cet article de leçon supplémentaire fait partie d’un didacticiel de modélisation tabulaire. Avant d’effectuer les tâches de cette leçon supplémentaire, vous devez avoir terminé toutes les leçons précédentes ou disposer d’un projet de modèle d’exemple Adventure Works Internet Sales terminé.  
  
## <a name="whats-the-issue"></a>Quel est le problème ?

Examinons les détails de la mesure InternetTotalSales avant d’ajouter une Expression de lignes de détail.

1.  Dans SSDT, cliquez sur le **modèle** menu > **analyser dans Excel** pour ouvrir Excel et créer un tableau croisé dynamique vide.
  
2.  Dans **PivotTable Fields**, ajoutez le **InternetTotalSales** mesure à partir de la table FactInternetSales à **valeurs**, **CalendarYear** à partir de la table DimDate à **colonnes**, et **EnglishCountryRegionName** à **lignes**. Le tableau croisé dynamique permet à présent les résultats agrégés à partir de la mesure InternetTotalSales par région et par année. 

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-pivottable.png)

3. Dans le tableau croisé dynamique, double-cliquez sur une valeur agrégée pour une année et un nom de région. Ici, nous avons double-cliqué sur la valeur pour l’Australie et de l’année 2014. Une nouvelle feuille s’ouvre, contenant des données, mais pas l’utilité.

    ![as-lesson-detail-rows-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-rows-sheet.png)
  
Nous voulons voir ici une table contenant des colonnes et lignes de données qui contribuent au résultat agrégé de la mesure InternetTotalSales. Pour ce faire, nous pouvons ajouter une Expression de lignes de détail en tant que propriété de la mesure.

## <a name="add-a-detail-rows-expression"></a>Ajouter une Expression de lignes de détail

#### <a name="to-create-a-detail-rows-expression"></a>Pour créer une Expression de lignes de détail 
  
1. Dans la grille de mesures de la table FactInternetSales, cliquez sur le **InternetTotalSales** mesure. 

2. Dans **propriétés** > **Expression de lignes de détail**, cliquez sur le bouton de l’éditeur pour ouvrir l’éditeur DAX.

    ![as-lesson-detail-rows-ellipse](../tutorial-tabular-1400/media/as-lesson-detail-rows-ellipse.png)

3. Dans l’éditeur DAX, entrez l’expression suivante :

    ```
    SELECTCOLUMNS(
    FactInternetSales,
    "Sales Order Number", FactInternetSales[SalesOrderNumber],
    "Customer First Name", RELATED(DimCustomer[FirstName]),
    "Customer Last Name", RELATED(DimCustomer[LastName]),
    "City", RELATED(DimGeography[City]),
    "Order Date", FactInternetSales[OrderDate],
    "Internet Total Sales", [InternetTotalSales]
    )

    ```

    Cette expression indique des noms, des colonnes et les résultats de mesure à partir de la table FactInternetSales et les tables associées sont retournés lorsqu’un utilisateur double-clique sur un résultat agrégé dans un tableau croisé dynamique ou un rapport.

4. De retour dans Excel, supprimez la feuille créée à l’étape 3, puis double-cliquez sur une valeur agrégée. Cette fois, avec une propriété d’Expression de lignes de détails définie pour la mesure, une nouvelle feuille s’ouvre contenant des données beaucoup plus utiles.

    ![as-lesson-detail-rows-detailsheet](../tutorial-tabular-1400/media/as-lesson-detail-rows-detailsheet.png)

5. Redéployez votre modèle.

  
## <a name="see-also"></a>Voir aussi  

[Selectcolumns, fonction (DAX)](/dax/selectcolumns-function-dax)  
[Leçon supplémentaire - Sécurité dynamique](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Leçon supplémentaire - Hiérarchies déséquilibrées](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)  
