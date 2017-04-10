---
title: "Le&#231;on 7 : Cr&#233;er des mesures | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 01bd2ad7-09b7-49ae-ad80-83f25da301aa
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Le&#231;on 7 : Cr&#233;er des mesures
Dans cette leçon, vous allez créer des mesures à inclure dans votre modèle. Similairement aux colonnes calculées que vous avez créées dans la leçon précédente, une mesure est essentiellement un calcul créé à l'aide d'une formule DAX. Toutefois, contrairement aux colonnes calculées, les mesures sont évaluées en fonction d'un *filtre*sélectionné par l'utilisateur ; par exemple, une colonne ou un segment particulier ajouté au champ des étiquettes de ligne dans un tableau croisé dynamique.   Une valeur pour chaque cellule dans le filtre est ensuite calculée par la mesure appliquée. Les mesures sont des calculs puissants et flexibles que vous pouvez inclure dans pratiquement tous les modèles tabulaires, pour effectuer des calculs dynamiques sur des données numériques. Pour plus d’informations, consultez [Mesures &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/measures-ssas-tabular.md).  
  
Pour créer des mesures, vous utilisez la grille de mesures. Par défaut, chaque table contient une grille de mesures vide ; toutefois, en général, vous ne créez pas de mesures pour chaque table. La grille de mesures s'affiche sous une table au sein du générateur de modèles dans la vue de données. Pour cacher ou afficher la grille de mesures d'une table, cliquez sur le menu **Table** , puis sur **Afficher la grille de mesures**.  
  
Vous pouvez créer une mesure en cliquant sur une cellule vide dans la grille de mesures, puis en tapant une formule DAX dans la barre de formule. Lorsque vous cliquez sur ENTRÉE pour terminer la formule, la mesure apparaît dans la cellule. Vous pouvez également créer des mesures à l’aide d’une fonction d’agrégation standard en cliquant sur une colonne, puis en cliquant sur le bouton de somme automatique (**∑**) dans la barre d’outils. Les mesures créées à l'aide de la fonction Somme automatique apparaissent dans la cellule de la grille de mesures, directement sous la colonne. Toutefois, elles peuvent être déplacées si nécessaire.  
  
Dans cette leçon, vous allez créer des mesures en entrant une formule DAX dans la barre de formule et en utilisant la fonction de somme automatique.  
  
Durée estimée pour effectuer cette leçon : **30 minutes**  
  
## Conditions préalables  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 6 : Créer des colonnes calculées](../analysis-services/lesson-6-create-calculated-columns.md).  
  
## Créer des mesures  
  
#### Pour créer une mesure pour tous les jours du trimestre en cours jusqu'à la date du jour dans la table de dates  
  
1.  Dans le concepteur de modèles, cliquez sur la table **Date** .  
  
2.  Si une grille de mesures vide n'apparaît pas sous la table, cliquez sur le menu **Table** , puis cliquez sur **Afficher la grille de mesures**.  
  
3.  Dans la grille de mesures, cliquez sur la cellule vide en haut à gauche.  
  
4.  Dans la barre de formule au-dessus de la table, tapez la formule suivante :  
  
    **=COUNTROWS( DATESQTD( 'Date'[Date]))**  
  
    Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
    Notez que la cellule en haut à gauche contient maintenant une mesure nommée **Measure 1**, suivie du résultat, **92**. Le nom de la mesure précède également la formule dans la barre de formule.  
  
5.  Pour renommer la mesure, dans la barre de formule, mettez en surbrillance le nom, **Mesure 1**, puis tapez **Jours du trimestre en cours à ce jour**, puis appuyez sur ENTRÉE.  
  
    > [!TIP]  
    > Quand vous tapez une formule dans la barre de formule, vous pouvez également taper d’abord le nom de la mesure suivi de deux-points (:), puis suivi de la formule. Avec cette méthode, vous n'aurez pas à renommer la mesure.  
  
#### Pour créer une mesure pour tous les jours du trimestre en cours dans la table de dates  
  
1.  Lorsque la table **Date** est active dans le concepteur de modèles, dans la grille de mesures, cliquez sur la cellule vide sous la mesure que vous venez de créer.  
  
2.  Dans la barre de formule, entrez la formule suivante :  
  
    **Days in Current Quarter :=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))**  
  
    Notez que dans cette formule vous avez inclus d'abord le nom de la mesure suivi du signe deux-points (:).  
  
    Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
Lorsque vous créez un ratio de comparaison entre une période incomplète et la période précédente, la formule doit prendre en compte la partie de la période qui s'est écoulée, et la comparer à la même partie de la période précédente. Dans ce cas, [Jours du trimestre en cours à ce jour] /[Jours du trimestre en cours] donne la période écoulée dans la période actuelle.  
  
#### Pour créer une mesure de comptage de valeurs de commande client dans la table Internet Sales  
  
1.  Dans le concepteur de modèles, cliquez sur la table **Internet Sales** (onglet).  
  
    Si la grille de mesures n’apparaît pas, cliquez avec le bouton droit sur la table **Internet Sales** (onglet), puis cliquez sur **Afficher la grille de mesures**.  
  
2.  Cliquez sur l'en-tête de colonne **Sales Order Number** .  
  
3.  Dans la barre d’outils, cliquez sur la flèche du bas en regard du bouton de somme automatique (**∑**), puis sélectionnez **DistinctCount**.  
  
    La fonction de somme automatique crée automatiquement une mesure pour la colonne sélectionnée à l'aide de la formule de regroupement standard DistinctCount.  
  
    Notez que la cellule supérieure sous la colonne dans la grille de mesures contient maintenant une mesure de nom, **Distinct Count Sales Order Number**. Les mesures créées à l'aide de la fonction de somme automatique sont automatiquement placées dans la cellule supérieure de la grille de mesures, sous la colonne associée.  
  
4.  Dans la grille de mesures, cliquez sur la nouvelle mesure, puis dans la fenêtre **Propriétés** , dans **Nom de la mesure**, renommez la mesure en **Internet Distinct Count Sales Order**.  
  
#### Pour créer des mesures supplémentaires dans la table Internet Sales  
  
1.  En utilisant la fonction de somme automatique, créez et nommez les mesures suivantes :  
  
    |Nom de la mesure|Colonne|Somme automatique (∑)|Formule|  
    |----------------|----------|-----------------|-----------|  
    |Internet Order Lines Count|Sales Order Line Number|Compter|=COUNT([Sales Order Line Number])|  
    |Internet Total Units|Order Quantity|Sum|=SUM([Order Quantity])|  
    |Internet Total Discount Amount|Discount Amount|Sum|=SUM([Discount Amount])|  
    |Internet Total Product Cost|Total Product Cost|Sum|=SUM([Total Product Cost])|  
    |Internet Total Sales|Sales Amount|Sum|=SUM([Sales Amount])|  
    |Internet Total Margin|Margin|Sum|=SUM([Margin])|  
    |Internet Total Tax Amt|Tax Amt|Sum|=SUM([Tax Amt])|  
    |Internet Total Freight|Freight|Sum|=SUM([Freight])|  
  
2.  En cliquant sur une cellule vide dans la grille de mesures, et à l'aide de la barre de formule, créez et nommez les mesures suivantes :  
  
    > [!IMPORTANT]  
    > Vous devez créer les mesures suivantes dans l'ordre ; les formules dans les mesures ultérieures font référence aux mesures précédentes.  
  
    |Nom de la mesure|Formule|  
    |----------------|-----------|  
    |Internet Previous Quarter Margin|=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))|  
    |Internet Current Quarter Margin|=TOTALQTD([Internet Total Margin],'Date'[Date])|  
    |Internet Previous Quarter Margin Proportion to QTD|=[Internet Previous Quarter Margin]*([Days Current Quarter to Date]/[Days In Current Quarter])|  
    |Internet Previous Quarter Sales|=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))|  
    |Internet Current Quarter Sales|=TOTALQTD([Internet Total Sales],'Date'[Date])|  
    |Internet Previous Quarter Sales Proportion to QTD|=[Internet Previous Quarter Sales]*([Days Current Quarter to Date]/[Days In Current Quarter])|  
  
Les mesures créées pour la table Internet Sales peuvent être utilisées pour analyser des données financières critiques telles que les ventes, les coûts et la marge bénéficiaire des éléments définis par le filtre sélectionné par l'utilisateur.  
  
## Étape suivante  
Pour continuer ce didacticiel, passez à la leçon suivante : [Leçon 8 : Créer les indicateurs de performance clés](../analysis-services/lesson-8-create-key-performance-indicators.md).  
  
  
  
