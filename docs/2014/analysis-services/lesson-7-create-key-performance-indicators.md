---
title: 'Leçon 8 : créer des indicateurs de performance clés | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d9d3145583670fb849321bac5b57928caacfbc2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078370"
---
# <a name="lesson-8-create-key-performance-indicators"></a>Leçon 8 : Créer les indicateurs de performance clés
  Au cours de cette leçon, vous allez créer des indicateurs de performance clés (KPI). Les indicateurs de performance clés sont utilisés pour évaluer les performances d’une valeur, définie par une mesure de *base* , par rapport à une valeur *cible* , également définie par une mesure ou par une valeur absolue. Dans les applications clientes de création de rapports, les indicateurs de performance clés offrent aux professionnels un moyen d’obtenir rapidement et aisément un résumé d’un succès commercial ou d’identifier les tendances. Pour en savoir plus, consultez [KPI &#40;SSAS Tabulaire&#41;](tabular-models/kpis-ssas-tabular.md).  
  
 Durée estimée pour suivre cette leçon : **15 minutes**  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique fait partie d’un didacticiel de modélisation tabulaire, qui doit être suivi dans l’ordre prévu. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la [Leçon 7 : Créer des mesures](lesson-6-create-measures.md).  
  
## <a name="create-key-performance-indicators"></a>Créer des indicateurs de performance clés (KPI)  
  
#### <a name="to-create-an-internet-current-quarter-sales-performance-kpi"></a>Pour créer un KPI des performances des ventes Internet du trimestre en cours  
  
1.  Dans le concepteur de modèles, cliquez sur la table **Internet Sales** (onglet).  
  
2.  Dans la grille de mesure, cliquez sur une cellule vide.  
  
3.  Dans la barre de formule située au-dessus de la table, tapez la formule suivante :  
  
     `Internet Current Quarter Sales Performance :=IFERROR([Internet Current Quarter Sales]/[Internet Previous Quarter Sales Proportion to QTD],BLANK())`  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
     Cette mesure servira de mesure de base pour l’indicateur de performance clé.  
  
4.  Dans la grille de mesures, cliquez avec le bouton droit sur la mesure **Internet Current Quarter Sales Performance**, puis cliquez sur **Créer un KPI**.  
  
     La boîte de dialogue **Indicateur de performance clé** s’affiche.  
  
5.  Dans la boîte de dialogue **Indicateur de performance clé**, dans **Définir la valeur cible**, sélectionnez l’option **Valeur absolue**.  
  
6.  Dans le champ **valeur absolue** , tapez `1.1`, puis appuyez sur entrée.  
  
7.  Dans **définir les seuils d’État**, dans le champ curseur de gauche (bas) `1`, tapez, puis dans le champ curseur de droite (élevé), `1.07`tapez.  
  
8.  Dans **Sélectionnez le style d’icône**, sélectionnez le losange (rouge), le triangle (jaune) ou le cercle (vert) comme type d’icône.  
  
    > [!TIP]  
    >  Notez que le champ extensible **Descriptions** apparaît sous les styles d’icône disponibles. Vous pouvez taper une description des différents éléments KPI afin de mieux les identifier dans les applications clientes.  
  
9. Cliquez sur **OK** pour terminer l’indicateur KPI.  
  
     Dans la grille de mesures, notez l’icône située à côté de la mesure **Internet Current Quarter Sales Performance**. Cette icône indique que cette mesure sert de valeur de base pour un indicateur KPI.  
  
#### <a name="to-create-an-internet-current-quarter-margin-performance-kpi"></a>Pour créer un KPI des performances des marges Internet du trimestre en cours  
  
1.  Dans la grille de mesures pour la table **Internet Sales**, cliquez sur une cellule vide.  
  
2.  Dans la barre de formule située au-dessus de la table, tapez la formule suivante :  
  
     `Internet Current Quarter Margin Performance :=IF([Internet Previous Quarter Margin Proportion to QTD]<>0,([Internet Current Quarter Margin]-[Internet Previous Quarter Margin Proportion to QTD])/[Internet Previous Quarter Margin Proportion to QTD],BLANK())`  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
3.  Dans la grille de mesures, cliquez avec le bouton droit sur la mesure **Internet Current Quarter Margin Performance**, puis cliquez sur **Créer un KPI**.  
  
4.  Dans la boîte de dialogue **Indicateur de performance clé**, dans **Définir la valeur cible**, sélectionnez l’option **Valeur absolue**.  
  
5.  Dans le champ **valeur absolue** , tapez `1.25`.  
  
6.  Dans **Définir les seuils d’état**, faites glisser le secteur gauche (bas) du curseur jusqu’à ce que le champ affiche **0.8**, puis faites glisser le secteur droit (élevé) du curseur jusqu’à ce que le champ affiche **1.03**.  
  
7.  Dans **Sélectionnez le style d’icône**, sélectionnez le losange (rouge), le triangle (jaune) ou le cercle (vert) comme type d’icône, puis cliquez sur **OK**.  
  
## <a name="next-step"></a>étape suivante  
 Pour continuer ce didacticiel, passez à la [Leçon 9 : Créer des perspectives](lesson-8-create-perspectives.md).  
  
  
