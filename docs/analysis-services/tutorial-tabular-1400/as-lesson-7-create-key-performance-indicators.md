---
title: 'Analysis Services leçon du didacticiel 7 : Créer des indicateurs de Performance clés | Microsoft Docs'
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
ms.openlocfilehash: 5f3b3de71cb60a27613482255556bfbff6bcc8cf
ms.sourcegitcommit: 6193aa9b4967302424270d67c27dbc601ca6849a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877619"
---
# <a name="create-key-performance-indicators"></a>Créer des indicateurs de performance clé (KPI)

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon, vous créez des indicateurs de Performance clés (KPI). Indicateurs de performance clés sont utilisés pour mesurer les performances d’une valeur définie par un *Base* mesure, par rapport à un *cible* valeur également définie par une mesure ou par une valeur absolue. Dans les applications clientes de création de rapports, les indicateurs de performance clés offrent aux professionnels un moyen d'obtenir rapidement et aisément un récapitulatif d'un succès commercial ou d'identifier les tendances. Pour plus d’informations, consultez [indicateurs de performance clés](../tabular-models/kpis-ssas-tabular.md)
  
Durée estimée pour effectuer cette leçon : **15 minutes**  
  
## <a name="prerequisites"></a>Prérequis  

Cet article fait partie d’un didacticiel de modélisation tabulaire, qui doit être effectué dans l’ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 6 : Créer des mesures](../tutorial-tabular-1400/as-lesson-6-create-measures.md).   
  
## <a name="create-key-performance-indicators"></a>Créer des indicateurs de performance clé (KPI)  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>Pour créer un KPI InternetCurrentQuarterSalesPerformance  
  
1.  Dans le Concepteur de modèles, cliquez sur le **FactInternetSales** table.  
  
2.  Dans la grille de mesures, cliquez sur une cellule vide.  
  
3.  Dans la barre de formule au-dessus de la table, tapez la formule suivante : 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=IF([InternetPreviousQuarterSalesProportionToQTD]<>0,([InternetCurrentQuarterSales]-[InternetPreviousQuarterSalesProportionToQTD])/[InternetPreviousQuarterSalesProportionToQTD],BLANK()) 
    ```

    Cette mesure sert de mesure de Base pour l’indicateur de performance clé.  
  
4.  Dans la grille de mesures, cliquez sur **InternetCurrentQuarterSalesPerformance** > **créer un KPI**.   
  
5.  Dans la boîte de dialogue indicateur de Performance clé (KPI) dans **cible** sélectionnez **valeur absolue**, puis tapez **1.1**.  
  
7.  Dans le secteur gauche (bas) du curseur, tapez **1**, puis dans le secteur droit (élevé) du curseur, tapez **1.07**.  
  
8.  Dans **Sélectionner le style d’icône**, sélectionnez le type d’icône losange (rouge), triangle (jaune) et cercle (vert).
  
    ![as-lesson7-kpi](../tutorial-tabular-1400/media/as-lesson7-kpi.png)
    
    > [!TIP]  
    > Notez l’extensible **Descriptions** étiquette sous les styles d’icône disponibles. Utilisez les descriptions des différents éléments KPI pour les rendre plus identifiables dans les applications clientes.  
  
9. Cliquez sur **OK** pour terminer le KPI.  
  
    Dans la grille de mesures, remarquez l’icône en regard du **InternetCurrentQuarterSalesPerformance** mesure. Cette icône indique que cette mesure sert de valeur de base à un indicateur de performance clé.  
  
#### <a name="to-create-an-internetcurrentquartermarginperformance-kpi"></a>Pour créer un KPI InternetCurrentQuarterMarginPerformance  
  
1.  Dans la grille de mesures pour le **FactInternetSales** , cliquez sur une cellule vide.  
  
2.  Dans la barre de formule au-dessus de la table, tapez la formule suivante :  

    ```
    InternetCurrentQuarterMarginPerformance :=IF([InternetPreviousQuarterMarginProportionToQTD]<>0,([InternetCurrentQuarterMargin]-[InternetPreviousQuarterMarginProportionToQTD])/[InternetPreviousQuarterMarginProportionToQTD],BLANK())  
    ```
 
3.  Avec le bouton droit **InternetCurrentQuarterMarginPerformance** > **créer un KPI**.  
  
4.  Dans la boîte de dialogue indicateur de Performance clé (KPI) dans **cible** sélectionnez **valeur absolue**, puis tapez **1,25**.   
  
5.  Dans le champ de gauche (bas) du curseur, faites glisser le curseur jusqu'à ce que le champ affiche **0.8**, puis faites glisser le curseur droit (élevé), jusqu'à ce que le champ affiche **1.03**.  
  
6.  Dans **Sélectionner le style d’icône**, sélectionnez le type d’icône losange (rouge), triangle (jaune) et cercle (vert), puis cliquez sur **OK**.  
  
## <a name="whats-next"></a>Quelle est l’étape suivante ?

[Leçon 8 : Créer des perspectives](../tutorial-tabular-1400/as-lesson-8-create-perspectives.md).
  
  
