---
title: "Le&#231;on&#160;8&#160;: Cr&#233;er les indicateurs de performance cl&#233;s | Microsoft Docs"
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
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Le&#231;on&#160;8&#160;: Cr&#233;er les indicateurs de performance cl&#233;s
Au cours de cette leçon, vous allez créer des indicateurs de performance clés (KPI). Les KPI évaluent la performance d’une valeur, définie par une mesure de *base*, par rapport à une valeur *cible*, également définie par une mesure ou par une valeur absolue. Dans les applications clientes de création de rapports, les indicateurs de performance clés offrent aux professionnels un moyen d'obtenir rapidement et aisément un récapitulatif d'un succès commercial ou d'identifier les tendances. Pour en savoir plus, consultez [KPI &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/kpis-ssas-tabular.md).  
  
Durée estimée pour effectuer cette leçon : **15 minutes**  
  
## Conditions préalables  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la [Leçon 7 : Créer des mesures](../analysis-services/lesson-7-create-measures.md).  
  
## Créer des indicateurs de performance clé (KPI)  
  
#### Pour créer un KPI des performances des ventes Internet du trimestre en cours  
  
1.  Dans le concepteur de modèles, cliquez sur la table **Internet Sales** (onglet).  
  
2.  Dans la grille de mesures, cliquez sur une cellule vide.  
  
3.  Dans la barre de formule au-dessus de la table, tapez la formule suivante :  
  
    **Internet Current Quarter Sales Performance :=IFERROR([Internet Current Quarter Sales]/[Internet Previous Quarter Sales Proportion to QTD],BLANK())**  
  
    Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
    Cette mesure servira de mesure de base à l'indicateur de performance clé.  
  
4.  Dans la grille de mesures, cliquez avec le bouton droit sur la mesure **Internet Current Quarter Sales Performance**, puis cliquez sur **Créer un KPI**.  
  
    La boîte de dialogue **Indicateur de performance clé** s’affiche.  
  
5.  Dans la boîte de dialogue **Indicateur de performance clé**, dans **Définir la valeur cible**, sélectionnez l’option **Valeur absolue**.  
  
6.  Dans le champ **Valeur absolue**, tapez **1.1**, puis appuyez sur Entrée.  
  
7.  Dans le secteur gauche (bas) du curseur, tapez **1**, puis dans le secteur droit (élevé) du curseur, tapez **1.07**.  
  
8.  Dans **Sélectionner le style d’icône**, sélectionnez le type d’icône losange (rouge), triangle (jaune) et cercle (vert).  
  
    > [!TIP]  
    > Notez que le champ extensible **Descriptions** apparaît sous les styles d’icône disponibles. Vous pouvez taper une description des différents éléments KPI afin de mieux les identifier dans les applications clientes.  
  
9. Cliquez sur **OK** pour terminer le KPI.  
  
    Dans la grille de mesures, notez l’icône située à côté de la mesure **Internet Current Quarter Sales Performance**. Cette icône indique que cette mesure sert de valeur de base à un indicateur de performance clé.  
  
#### Pour créer un KPI des performances des marges Internet du trimestre en cours  
  
1.  Dans la grille de mesures pour la table **Internet Sales**, cliquez sur une cellule vide.  
  
2.  Dans la barre de formule au-dessus de la table, tapez la formule suivante :  
  
    **Internet Current Quarter Margin Performance :=IF([Internet Previous Quarter Margin Proportion to QTD]<>0,([Internet Current Quarter Margin]-[Internet Previous Quarter Margin Proportion to QTD])/[Internet Previous Quarter Margin Proportion to QTD],BLANK())**  
  
    Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
3.  Dans la grille de mesures, cliquez avec le bouton droit sur la mesure **Internet Current Quarter Margin Performance**, puis cliquez sur **Créer un KPI**.  
  
4.  Dans la boîte de dialogue **Indicateur de performance clé**, dans **Définir la valeur cible**, sélectionnez l’option **Valeur absolue**.  
  
5.  Dans le champ **Valeur absolue**, tapez **1.25**.  
  
6.  Dans **Définir les seuils d’état**, faites glisser le secteur gauche (bas) du curseur jusqu’à ce que le champ affiche **0.8**, puis faites glisser le secteur droit (élevé) du curseur jusqu’à ce que le champ affiche **1.03**.  
  
7.  Dans **Sélectionner le style d’icône**, sélectionnez le type d’icône losange (rouge), triangle (jaune) et cercle (vert), puis cliquez sur **OK**.  
  
## Étape suivante  
Pour continuer ce didacticiel, passez à la [Leçon 9 : Créer des perspectives](../Topic/Lesson%209:%20Create%20Perspectives.md).  
  
  
  
