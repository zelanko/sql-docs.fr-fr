---
title: 'Leçon du didacticiel Analysis Services 7 : créer des indicateurs de Performance clés | Documents Microsoft'
description: Décrit comment créer des indicateurs de Performance clés dans le projet du didacticiel Analysis Services.
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: b5baa301f8e9162205b4995e557f3178107a0fcc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="create-key-performance-indicators"></a>Créer des indicateurs de performance clé (KPI)

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon, vous créez des indicateurs de Performance clés (KPI). Indicateurs de performance clés sont utilisées pour mesurer les performances d’une valeur définie par un *Base* mesure, par rapport à un *cible* valeur également définie par une mesure ou par une valeur absolue. Dans les applications clientes de création de rapports, les indicateurs de performance clés offrent aux professionnels un moyen d'obtenir rapidement et aisément un récapitulatif d'un succès commercial ou d'identifier les tendances. Pour plus d’informations, consultez [indicateurs de performance clés](../tabular-models/kpis-ssas-tabular.md)
  
Durée estimée pour effectuer cette leçon : **15 minutes**  
  
## <a name="prerequisites"></a>Configuration requise  

Cet article fait partie d’un didacticiel de modélisation tabulaire, qui doit être effectué dans l’ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 6 : créer des mesures](../tutorial-tabular-1400/as-lesson-6-create-measures.md).   
  
## <a name="create-key-performance-indicators"></a>Créer des indicateurs de performance clé (KPI)  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>Pour créer un KPI InternetCurrentQuarterSalesPerformance  
  
1.  Dans le Générateur de modèles, cliquez sur le **FactInternetSales** table.  
  
2.  Dans la grille de mesures, cliquez sur une cellule vide.  
  
3.  Dans la barre de formule au-dessus de la table, tapez la formule suivante : 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=DIVIDE([InternetCurrentQuarterSales]/[InternetPreviousQuarterSalesProportionToQTD],BLANK())  
    ```

    Cette mesure sert de mesure de Base pour l’indicateur de performance clé.  
  
4.  Dans la grille de mesures, cliquez sur **InternetCurrentQuarterSalesPerformance** > **créer un KPI**.   
  
5.  Dans la boîte de dialogue indicateur de Performance clé (KPI) dans **cible** sélectionnez **valeur absolue**, puis tapez **1.1**.  
  
7.  Dans le secteur gauche (bas) du curseur, tapez **1**, puis dans le secteur droit (élevé) du curseur, tapez **1.07**.  
  
8.  Dans **Sélectionner le style d’icône**, sélectionnez le type d’icône losange (rouge), triangle (jaune) et cercle (vert).
  
    ![as-lesson7-kpi](../tutorial-tabular-1400/media/as-lesson7-kpi.png)
    
    > [!TIP]  
    > Notez l’extensible **Descriptions** étiquette sous les styles d’icônes disponibles. Utilisez les descriptions pour les différents éléments de l’indicateur de performance clé pour les rendre plus identifiable dans les applications clientes.  
  
9. Cliquez sur **OK** pour terminer le KPI.  
  
    Dans la grille de mesures, remarquez l’icône en regard du **InternetCurrentQuarterSalesPerformance** mesure. Cette icône indique que cette mesure sert de valeur de base à un indicateur de performance clé.  
  
#### <a name="to-create-an-internetcurrentquartermarginperformance-kpi"></a>Pour créer un KPI InternetCurrentQuarterMarginPerformance  
  
1.  Dans la grille de mesures pour le **FactInternetSales** , cliquez sur une cellule vide.  
  
2.  Dans la barre de formule au-dessus de la table, tapez la formule suivante :  

    ```
    InternetCurrentQuarterMarginPerformance :=IF([InternetPreviousQuarterMarginProportionToQTD]<>0,([InternetCurrentQuarterMargin]-[InternetPreviousQuarterMarginProportionToQTD])/[InternetPreviousQuarterMarginProportionToQTD],BLANK())  
    ```
 
3.  Avec le bouton droit **InternetCurrentQuarterMarginPerformance** > **créer un KPI**.  
  
4.  Dans la boîte de dialogue indicateur de Performance clé (KPI) dans **cible** sélectionnez **valeur absolue**, puis tapez **1.25**.   
  
5.  Dans le champ de gauche (bas) du curseur, faites glisser jusqu'à ce que le champ affiche **0,8**, puis faites glisser le curseur droit (élevé) champ, jusqu'à ce que le champ affiche **1.03**.  
  
6.  Dans **Sélectionner le style d’icône**, sélectionnez le type d’icône losange (rouge), triangle (jaune) et cercle (vert), puis cliquez sur **OK**.  
  
## <a name="whats-next"></a>Quelle est l’étape suivante ?

[Leçon 8 : Créer des perspectives](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md).
  
  
