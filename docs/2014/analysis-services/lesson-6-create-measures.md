---
title: 'Leçon 7 : Créer des mesures | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01bd2ad7-09b7-49ae-ad80-83f25da301aa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ef207028ab1b4f6bc084f3f4e515ae37630b771d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66078428"
---
# <a name="lesson-7-create-measures"></a>Leçon 7 : Créer des mesures
  Dans cette leçon, vous allez créer des mesures à inclure dans votre modèle. Similairement aux colonnes calculées que vous avez créées dans la leçon précédente, une mesure est essentiellement un calcul créé à l'aide d'une formule DAX. Toutefois, contrairement aux colonnes calculées, les mesures sont évaluées en fonction d'un *filtre*sélectionné par l'utilisateur ; par exemple, une colonne ou un segment particulier ajouté au champ des étiquettes de ligne dans un tableau croisé dynamique.   Une valeur pour chaque cellule dans le filtre est ensuite calculée par la mesure appliquée. Les mesures sont des calculs puissants et flexibles que vous pouvez inclure dans pratiquement tous les modèles tabulaires, pour effectuer des calculs dynamiques sur des données numériques. Pour plus d’informations, consultez [Mesures &#40;SSAS Tabulaire&#41;](tabular-models/measures-ssas-tabular.md).  
  
 Pour créer des mesures, vous utilisez la grille de mesures. Par défaut, chaque table contient une grille de mesures vide ; toutefois, en général, vous ne créez pas de mesures pour chaque table. La grille de mesures s'affiche sous une table au sein du générateur de modèles dans la vue de données. Pour cacher ou afficher la grille de mesures d'une table, cliquez sur le menu **Table** , puis sur **Afficher la grille de mesures**.  
  
 Vous pouvez créer une mesure en cliquant sur une cellule vide dans la grille de mesures, puis en tapant une formule DAX dans la barre de formule. Lorsque vous cliquez sur ENTRÉE pour terminer la formule, la mesure apparaît dans la cellule. Vous pouvez également créer des mesures à l’aide d’une fonction d’agrégation standard en cliquant sur une colonne, puis en cliquant sur le bouton de somme automatique (**∑**) dans la barre d’outils. Les mesures créées à l'aide de la fonction Somme automatique apparaissent dans la cellule de la grille de mesures, directement sous la colonne. Toutefois, elles peuvent être déplacées si nécessaire.  
  
 Dans cette leçon, vous allez créer des mesures en entrant une formule DAX dans la barre de formule et en utilisant la fonction de somme automatique.  
  
 Durée estimée pour effectuer cette leçon : **30 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 6 : Créer des colonnes calculées](lesson-5-create-calculated-columns.md).  
  
## <a name="create-measures"></a>Créer des mesures  
  
#### <a name="to-create-a-days-current-quarter-to-date-measure-in-the-date-table"></a>Pour créer une mesure pour tous les jours du trimestre en cours jusqu'à la date du jour dans la table de dates  
  
1.  Dans le concepteur de modèles, cliquez sur la table **Date** .  
  
2.  Si une grille de mesures vide n'apparaît pas sous la table, cliquez sur le menu **Table** , puis cliquez sur **Afficher la grille de mesures**.  
  
3.  Dans la grille de mesures, cliquez sur la cellule vide en haut à gauche.  
  
4.  Dans la barre de formule au-dessus de la table, tapez la formule suivante :  
  
     `=COUNTROWS( DATESQTD( 'Date'[Date]))`  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
     Notez que la cellule en haut à gauche contient maintenant une mesure nommée **Measure 1**, suivie du résultat, **30**. Le nom de la mesure précède également la formule dans la barre de formule.  
  
5.  Pour renommer la mesure, dans la barre de formule, mettez en surbrillance le nom, **Measure 1**, puis tapez `Days Current Quarter to Date`, puis appuyez sur ENTRÉE.  
  
    > [!TIP]  
    >  Lorsque vous tapez une formule dans la barre de formule, vous pouvez également taper d'abord le nom de la mesure suivi de deux-points (:), suivi d'un espace, puis suivi de la formule. Avec cette méthode, vous n'aurez pas à renommer la mesure.  
  
#### <a name="to-create-a-days-in-current-quarter-measure-in-the-date-table"></a>Pour créer une mesure pour tous les jours du trimestre en cours dans la table de dates  
  
1.  Lorsque la table **Date** est active dans le concepteur de modèles, dans la grille de mesures, cliquez sur la cellule vide sous la mesure que vous venez de créer.  
  
2.  Dans la barre de formule, entrez la formule suivante :  
  
     `Days in Current Quarter :=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))`  
  
     Notez que dans cette formule vous avez inclus d'abord le nom de la mesure suivi du signe deux-points (:).  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
 Lorsque vous créez un ratio de comparaison entre une période incomplète et la période précédente, la formule doit prendre en compte la partie de la période qui s'est écoulée, et la comparer à la même partie de la période précédente. Dans ce cas, [Jours du trimestre en cours à ce jour] /[Jours du trimestre en cours] donne la période écoulée dans la période actuelle.  
  
#### <a name="to-create-an-internet-distinct-count-sales-order-measure-in-the-internet-sales-table"></a>Pour créer une mesure de comptage de valeurs de commande client dans la table Internet Sales  
  
1.  Dans le concepteur de modèles, cliquez sur la table **Internet Sales** (onglet).  
  
     Si la grille de mesures n’apparaît pas, cliquez avec le bouton droit sur la table **Internet Sales** (onglet), puis cliquez sur **Afficher la grille de mesures**.  
  
2.  Cliquez sur l'en-tête de colonne **Sales Order Number** .  
  
3.  Dans la barre d’outils, cliquez sur la flèche du bas en regard du bouton de somme automatique (**∑**), puis sélectionnez **DistinctCount**.  
  
     La fonction de somme automatique crée automatiquement une mesure pour la colonne sélectionnée à l'aide de la formule de regroupement standard DistinctCount.  
  
     Notez que la cellule supérieure sous la colonne dans la grille de mesures contient maintenant une mesure de nom, **Distinct Count Sales Order Number**. Les mesures créées à l'aide de la fonction de somme automatique sont automatiquement placées dans la cellule supérieure de la grille de mesures, sous la colonne associée.  
  
4.  Dans la grille de mesures, cliquez sur la nouvelle mesure, puis dans la fenêtre **Propriétés** , dans **Nom de la mesure**, renommez la mesure en **Internet Distinct Count Sales Order**.  
  
#### <a name="to-create-additional-measures-in-the-internet-sales-table"></a>Pour créer des mesures supplémentaires dans la table Internet Sales  
  
1.  En utilisant la fonction de somme automatique, créez et nommez les mesures suivantes :  
  
    |Nom de la mesure|colonne|Somme automatique (∑)|Formule|  
    |------------------|------------|-------------------|-------------|  
    |Internet Order Lines Count|Sales Order Line Number|Count|=COUNT([Sales Order Line Number])|  
    |Internet Total Units|Order Quantity|Sum|=SUM([Order Quantity])|  
    |Internet Total Discount Amount|Discount Amount|Sum|=SUM([Discount Amount])|  
    |Internet Total Product Cost|Total Product Cost|Sum|=SUM([Total Product Cost])|  
    |Internet Total Sales|Sales Amount|Sum|=SUM([Sales Amount])|  
    |Internet Total Margin|Margin|Sum|=SUM([Margin])|  
    |Internet Total Tax Amt|Tax Amt|Sum|=SUM([Tax Amt])|  
    |Internet Total Freight|Freight|Sum|=SUM([Freight])|  
  
2.  En cliquant sur une cellule vide dans la grille de mesures, et à l'aide de la barre de formule, créez et nommez les mesures suivantes :  
  
    > [!IMPORTANT]  
    >  Vous devez créer les mesures suivantes dans l'ordre ; les formules dans les mesures ultérieures font référence aux mesures précédentes.  
  
    |Nom de la mesure|Formule|  
    |------------------|-------------|  
    |Internet Previous Quarter Margin|=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))|  
    |Internet Current Quarter Margin|=TOTALQTD([Internet Total Margin],'Date'[Date])|  
    |Internet Previous Quarter Margin Proportion to QTD|=[Internet Previous Quarter Margin]*([Days Current Quarter to Date]/[Days In Current Quarter])|  
    |Internet Previous Quarter Sales|=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))|  
    |Internet Current Quarter Sales|=TOTALQTD([Internet Total Sales],'Date'[Date])|  
    |Internet Previous Quarter Sales Proportion to QTD|=[Internet Previous Quarter Sales]*([Days Current Quarter to Date]/[Days In Current Quarter])|  
  
 Les mesures créées pour la table Internet Sales peuvent être utilisées pour analyser des données financières critiques telles que les ventes, les coûts et la marge bénéficiaire des éléments définis par le filtre sélectionné par l'utilisateur.  
  
## <a name="next-step"></a>Étape suivante  
 Pour continuer ce didacticiel, passez à la leçon suivante : [Leçon 8 : Créer des indicateurs de Performance clés](lesson-7-create-key-performance-indicators.md).  
  
  
