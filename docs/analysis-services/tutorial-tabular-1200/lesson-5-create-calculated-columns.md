---
title: 'Leçon 5 : Créer des colonnes calculées | Microsoft Docs'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df9b5a6d490b33b9aea786290acb7454d0066453
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65404181"
---
# <a name="lesson-5-create-calculated-columns"></a>Leçon 5 : Créer des colonnes calculées
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

Dans cette leçon, vous allez créer des données dans votre modèle en ajoutant des colonnes calculées. Une colonne calculée est basée sur les données qui existent déjà dans votre modèle. Pour plus d’informations, consultez [Calculated Columns](../tabular-models/ssas-calculated-columns.md).  
  
Vous allez créer cinq nouvelles colonnes calculées dans trois tables différentes. Les étapes sont légèrement différentes pour chaque tâche. Il s'agit de montrer qu'il existe plusieurs façons de créer de nouvelles colonnes, de les renommer, puis de les placer à différents emplacements dans une table.  
  
Durée estimée pour effectuer cette leçon : **15 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 4 : Créer des relations](lesson-4-create-relationships.md). 
  
## <a name="create-calculated-columns"></a>Créer des colonnes calculées  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>Créer une colonne calculée MonthCalendar dans la table DimDate  
  
1.  Cliquez sur le **modèle** menu > **vue de modèle** > **vue données**.  
  
    Les colonnes calculées ne peuvent être créées qu'à l'aide du concepteur de modèles dans la vue de données.  
  
2.  Dans le Concepteur de modèles, cliquez sur le **DimDate** table (onglet).  
  
3.  Cliquez sur le **CalendarQuarter** en-tête de colonne, puis cliquez sur **insérer une colonne**.  
  
    Une nouvelle colonne nommée **Calculated Column 1** est insérée à gauche de la colonne **Calendar Quarter** .  
  
4.  Dans la barre de formule au-dessus de la table, tapez la formule suivante. La saisie semi-automatique vous aide à taper les noms complets de colonnes et de tables et répertorie les fonctions disponibles.  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    Des valeurs remplissent ensuite toutes les lignes de la colonne calculée. Si vous faites défiler la table vers le bas, vous remarquez que les lignes peuvent avoir des valeurs différentes pour cette colonne, en fonction des données figurant dans chaque ligne.    
  
5.  Renommer cette colonne **MonthCalendar**. 

    ![as-tabular-lesson5-newcolumn](media/as-tabular-lesson5-newcolumn.png) 
  
La colonne calculée MonthCalendar fournit un nom triable pour le mois.  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>Créer une colonne calculée DayOfWeek dans la table DimDate  
  
1.  Avec le **DimDate** table toujours active, cliquez sur le **colonne** menu, puis sur **ajouter une colonne**.  
  
2.  Dans la barre de formule, entrez la formule suivante :  
    
    ```
    =RIGHT(" " & FORMAT([DayNumberOfWeek],"#0"), 2) & " - " & [EnglishDayNameOfWeek]  
    ```
    
    Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE. La nouvelle colonne est ajoutée à droite de la table.  
  
3.  Renommez la colonne en **DayOfWeek**.  
  
4.  Cliquez sur l’en-tête de colonne, puis faites glisser la colonne entre la **EnglishDayNameOfWeek** colonne et le **DayNumberOfMonth** colonne.  
  
    > [!TIP]  
    > Déplacer les colonnes dans la table facilite la navigation.  
  
La colonne calculée DayOfWeek fournit un nom triable pour le jour de semaine.  
  
#### <a name="create-a-productsubcategoryname-calculated-column-in-the-dimproduct-table"></a>Créer une colonne calculée ProductSubcategoryName dans la table DimProduct  
  
  
1.  Dans le **DimProduct** table, faites défiler jusqu'à l’extrême droite de la table. Notez que la colonne la plus à droite est nommée **Add Column** (en italique), cliquez sur l’en-tête de colonne.  
  
2.  Dans la barre de formule, entrez la formule suivante.  
    
    ```
    =RELATED('DimProductSubcategory'[EnglishProductSubcategoryName])  
    ```
  
3.  Renommez la colonne en **ProductSubcategoryName**.  
  
La colonne calculée ProductSubcategoryName est utilisée pour créer une hiérarchie dans la table DimProduct, qui inclut les données de la colonne EnglishProductSubcategoryName de la table DimProductSubcategory. Les hiérarchies ne peuvent pas couvrir plusieurs tables. Vous allez créer des hiérarchies plus loin dans la leçon 9.  
  
#### <a name="create-a-productcategoryname-calculated-column-in-the-dimproduct-table"></a>Créer une colonne calculée ProductCategoryName dans la table DimProduct  
  
1.  Avec le **DimProduct** table toujours active, cliquez sur le **colonne** menu, puis sur **ajouter une colonne**.  
  
2.  Dans la barre de formule, entrez la formule suivante :  
  
    ```
    =RELATED('DimProductCategory'[EnglishProductCategoryName]) 
    ```
    
3.  Renommez la colonne en **ProductCategoryName**.  
  
La colonne calculée ProductCategoryName est utilisée pour créer une hiérarchie dans la table DimProduct, qui inclut les données de la colonne EnglishProductCategoryName de la table DimProductCategory. Les hiérarchies ne peuvent pas couvrir plusieurs tables.  
  
#### <a name="create-a-margin-calculated-column-in-the-factinternetsales-table"></a>Créer une colonne calculée Margin dans la table FactInternetSales  
  
1.  Dans le Concepteur de modèles, sélectionnez le **FactInternetSales** table.  
  
2.  Ajoutez une nouvelle colonne.  
  
3.  Dans la barre de formule, entrez la formule suivante :  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  Renommez la colonne en **Margin**.  
  
5.  Faites glisser la colonne entre la **SalesAmount** colonne et le **TaxAmt** colonne. 
 
      ![as-tabular-lesson5-newmargin](media/as-tabular-lesson5-newmargin.png)
      
    La colonne calculée Margin est utilisée pour analyser les marges pour chaque vente.  
  
## <a name="whats-next"></a>Quelle est l’étape suivante ?
Accédez à la leçon suivante : [Leçon 6 : Créer des mesures](lesson-6-create-measures.md).
  
  
  
