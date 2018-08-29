---
title: 'Analysis Services leçon 5 du didacticiel : créer des colonnes calculées | Microsoft Docs'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 58a7f38dbbe7a68668418db4d1bef16e08784a08
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43063858"
---
# <a name="create-calculated-columns"></a>Créer des colonnes calculées

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon, vous créez des données dans votre modèle en ajoutant des colonnes calculées. Vous pouvez créer des colonnes calculées (en tant que colonnes personnalisées) lorsque vous utilisez obtenir des données, à l’aide de l’éditeur de requête, ou ultérieurement dans le type de Concepteur de modèle que vous effectuez. Pour plus d’informations, consultez [des colonnes calculées](../tabular-models/ssas-calculated-columns.md).
  
Vous créez cinq colonnes calculées dans trois tables différentes. Les étapes sont légèrement différentes pour chaque tâche montrer qu’il existe plusieurs façons de créer des colonnes, de les renommer et de les placer dans différents emplacements dans une table.  

Cette leçon est également où vous utilisez tout d’abord les Expressions DAX (Data Analysis). DAX est un langage spécial permettant de créer des expressions de formule hautement personnalisables pour les modèles tabulaires. Dans ce didacticiel, vous utilisez DAX pour créer des colonnes calculées, les mesures et les filtres de rôle. Pour plus d’informations, consultez [DAX dans les modèles tabulaires](../tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md). 
  
Durée estimée pour effectuer cette leçon : **15 minutes**  
  
## <a name="prerequisites"></a>Prérequis  

Cet article fait partie d’un didacticiel de modélisation tabulaire, qui doit être effectué dans l’ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [leçon 4 : créer des relations](../tutorial-tabular-1400/as-lesson-4-create-relationships.md). 
  
## <a name="create-calculated-columns"></a>Créer des colonnes calculées  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>Créer une colonne calculée MonthCalendar dans la table DimDate  
  
1.  Cliquez sur le **modèle** menu > **vue de modèle** > **vue données**.  
  
    Les colonnes calculées ne peuvent être créées qu'à l'aide du concepteur de modèles dans la vue de données.  
  
2.  Dans le Concepteur de modèles, cliquez sur le **DimDate** table (onglet).  
  
3.  Cliquez sur le **CalendarQuarter** en-tête de colonne, puis cliquez sur **insérer une colonne**.  
  
    Une nouvelle colonne nommée **Calculated Column 1** est insérée à gauche de la colonne **Calendar Quarter** .  
  
4.  Dans la barre de formule au-dessus de la table, tapez la formule DAX suivante : la saisie semi-automatique vous aide à taper les noms qualifiés complets de colonnes et de tables et répertorie les fonctions qui sont disponibles.  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    Des valeurs remplissent ensuite toutes les lignes de la colonne calculée. Si vous faites défiler vers le bas le tableau, vous consultez lignes peuvent avoir des valeurs différentes pour cette colonne, en fonction des données dans chaque ligne.    
  
5.  Renommer cette colonne **MonthCalendar**. 

    ![en tant que-lesson5-nouvelle colonne](../tutorial-tabular-1400/media/as-lesson5-newcolumn.png) 
  
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
  
2.  Dans la barre de formule, entrez la formule suivante :  
    
    ```
    =RELATED('DimProductSubcategory'[EnglishProductSubcategoryName])  
    ```
  
3.  Renommez la colonne en **ProductSubcategoryName**.  
  
La colonne calculée ProductSubcategoryName est utilisée pour créer une hiérarchie dans la table DimProduct, qui inclut les données de la colonne EnglishProductSubcategoryName de la table DimProductSubcategory. Les hiérarchies ne peuvent pas couvrir plusieurs tables. Créer des hiérarchies plus loin dans la leçon 9.  
  
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
  
2.  Créer une nouvelle colonne calculée entre la **SalesAmount** colonne et le **TaxAmt** colonne.  
  
3.  Dans la barre de formule, entrez la formule suivante :  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  Renommez la colonne en **Margin**.  
 
      ![en tant que newmargin de lesson5](../tutorial-tabular-1400/media/as-lesson5-newmargin.png)
      
    La colonne calculée Margin est utilisée pour analyser les marges pour chaque vente.  
  
## <a name="whats-next"></a>Quelle est l’étape suivante ?

[Leçon 6 : Créer des mesures](../tutorial-tabular-1400/as-lesson-6-create-measures.md).
  
  
  
