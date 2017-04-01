---
title: "Cr&#233;er et g&#233;rer les indicateurs de performance cl&#233;s (SSAS Tabulaire) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.kpi.f1"
ms.assetid: c96026c2-4394-4c3c-986b-4c95a4421900
caps.latest.revision: 15
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 15
---
# Cr&#233;er et g&#233;rer les indicateurs de performance cl&#233;s (SSAS Tabulaire)
  Cette rubrique décrit comment créer, modifier ou supprimer un indicateur de performance clé (KPI) dans un modèle tabulaire. Pour créer un indicateur de performance clé (KPI), sélectionnez une mesure qui donne la valeur de base de l'indicateur de performance clé. Utilisez ensuite la boîte de dialogue Indicateur de performance clé pour sélectionner une seconde mesure ou une valeur absolue qui prend une valeur cible. Vous pourrez ensuite définir des seuils d'état qui mesurent les performances entre les mesures de base et cible.  
  
 Cette rubrique inclut les tâches suivantes :  
  
-   [Pour créer un KPI](#bkmk_create_KPI)  
  
-   [Pour modifier un KPI](#bkmk_edit_KPI)  
  
-   [Pour supprimer un KPI et la mesure de base](#bkmk_delete)  
  
-   [Pour supprimer un KPI, mais conserver la mesure de base](#bkmk_delete_KPI)  
  
## Tâches  
  
> [!IMPORTANT]  
>  Avant de créer un KPI, vous devez d'abord créer une mesure de base qui retourne une valeur. La mesure de base doit ensuite être étendue à un KPI. Pour savoir comment créer des mesures, consultez la rubrique [Créer et gérer des mesures &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md). Un KPI nécessite également une valeur cible. Cette valeur peut être obtenue à partir d'une autre valeur prédéfinie ou d'une valeur absolue. Une fois que vous avez étendu une mesure de base à un KPI, vous pouvez sélectionner la valeur cible et définir les seuils d’état dans la boîte de dialogue Indicateur de performance clé.  
  
###  <a name="bkmk_create_KPI"></a> Pour créer un KPI  
  
1.  Dans la Grille de mesures, cliquez avec le bouton droit sur la mesure qui sert de mesure de base (valeur), puis cliquez sur **Créer un KPI**.  
  
2.  Dans la boîte de dialogue **Indicateur de performance clé**, dans **Définir la valeur cible**, sélectionnez l’une des options suivantes :  
  
     Sélectionnez **Mesure**, puis sélectionnez une mesure cible dans la zone de liste.  
  
     Sélectionnez **Valeur absolue**, puis entrez une valeur numérique.  
  
3.  Dans **Définir les seuils d’état**, cliquez sur les valeurs des seuils et faites-les glisser.  
  
4.  Dans **Sélectionner le style d’icône**, cliquez sur un type d’image.  
  
5.  Cliquez sur **Descriptions**, puis tapez une description du KPI, de la valeur, de l’état et de la cible.  
  
> [!TIP]  
>  Vous pouvez utiliser la fonctionnalité Analyser dans Excel pour tester votre indicateur de performance clé. Pour plus d’informations, consultez [Analyser dans Excel &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md).  
  
###  <a name="bkmk_edit_KPI"></a> Pour modifier un KPI  
  
-   Dans la grille de mesures, cliquez avec le bouton droit sur la mesure qui sert de mesure de base (valeur) du KPI, puis cliquez sur **Modifier les paramètres du KPI**.  
  
###  <a name="bkmk_delete"></a> Pour supprimer un KPI et la mesure de base  
  
-   Dans la grille de mesures, cliquez avec le bouton droit sur la mesure qui sert de mesure de base (valeur) du KPI, puis cliquez sur **Supprimer**.  
  
###  <a name="bkmk_delete_KPI"></a> Pour supprimer un KPI, mais conserver la mesure de base  
  
-   Dans la grille de mesures, cliquez avec le bouton droit sur la mesure qui sert de mesure de base (valeur) du KPI, puis cliquez sur **Supprimer le KPI**.  
  
## Raccourcis Alt  
  
|Section de l'interface utilisateur|Combinaison de touches|  
|----------------|-----------------|  
|Mesure de base du KPI|Alt+B|  
|État du KPI|Alt+S|  
|Measure|Alt+M|  
|Valeur absolue|Alt+A|  
|Définir les seuils d'état|Alt+U|  
|Sélectionner le style d'icône|Alt+I|  
|Tendance|Alt+T|  
|Descriptions|Alt+D|  
|Tendance|Alt+T|  
  
## Voir aussi  
 [Indicateurs de performance clés &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/kpis-ssas-tabular.md)   
 [Mesures &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [Créer et gérer des mesures &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)  
  
  