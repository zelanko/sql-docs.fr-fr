---
title: Filtre de modèle de règles d’une règle dans une Association | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 28d3601b18f792b957627e63630806453d971110
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209992"
---
# <a name="filter-a-rule-in-an-association-rules-model"></a>Filtrer une règle dans un modèle de règles d'association
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Vous pouvez utiliser le filtrage avec des modèles d'association pour restreindre les résultats aux associations qui vous intéressent. Par exemple, vous pouvez filtrer les règles pour afficher uniquement celles qui incluent un produit spécifique.  
  
 Dans le Concepteur d’exploration de données, vous pouvez utiliser les contrôles sur l’onglet **Règles** de la Visionneuse de l’algorithme MAR (Microsoft Association Rules) [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour filtrer les règles affichées.  Vous pouvez également créer une requête sur le modèle pour voir uniquement le jeu d’éléments contenant une valeur particulière.  
  
> [!NOTE]  
>  Cette option est disponible uniquement pour les modèles d'exploration de données créés à l'aide de l'algorithme Microsoft Association.  
  
### <a name="filter-a-rule-in-an-association-model"></a>Filtrer une règle dans un modèle d'association  
  
1.  Ouvrez le modèle d'exploration de données à l'aide de la **Visionneuse de l'algorithme MAR (Microsoft Association Rules)** . Pour ce faire, dans SQL Server Management Studio, cliquez avec le bouton droit sur le nom du modèle, puis sélectionnez **Parcourir**. Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], double-cliquez sur la structure d’exploration de données qui contient le modèle, puis cliquez sur l’onglet **Visionneuse de modèle d’exploration de données** du **Concepteur d’exploration de données**.  
  
2.  Cliquez sur l'onglet **Règles** de la **Visionneuse de l'algorithme MAR (Microsoft Association Rules)** .  
  
3.  Tapez une condition de règle dans la zone **Filtrer la règle** . Voici par exemple une condition de règle « Bike Stand », qui retourne également « Bike Stands ».  
  
     La zone de texte **Filtrer la règle** prend en charge les expressions régulières définies par le langage .NET. Par conséquent, vous pouvez utiliser des expressions telles que `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`. Cette expression retourne les jeux d'éléments qui incluent des attributs avec les mots Helmets et Fenders, dans n'importe quel ordre.  
  
4.  Pour **Probabilité minimale**, augmentez la valeur de probabilité afin de voir moins de règles ou réduisez cette valeur afin de voir davantage de règles.  
  
5.  Pour **Importance minimale**, augmentez la valeur d'importance afin de voir moins de règles ou réduisez cette valeur afin de voir davantage de règles.  
  
6.  Pour **afficher**, sélectionnez une des options suivantes : **Afficher le nom de l’attribut et valeur**, **afficher uniquement le nom attribut**, ou **afficher la valeur de l’attribut uniquement**.  
  
7.  Pour **Lignes au maximum**, augmentez la valeur afin d'augmenter le nombre total de règles répondant aux conditions spécifiées ou réduisez la valeur afin de limiter le nombre de règles retournées. Les règles sont classées par ordre de probabilité ; par conséquent, vous risquez d'éliminer des règles supplémentaires qui répondent aux conditions spécifiées pour la probabilité ou l'importance.  
  
8.  Activez ou désactivez la case à cocher **Afficher le nom long** pour basculer entre les modes d'affichage des noms de règles.  
  
     Les règles sont alors filtrées afin d'afficher uniquement celles qui contiennent l'élément indiqué. La condition de filtre s'applique aux valeurs d'attributs avant ou après le délimiteur de règle, « -> ».  
  
    > [!NOTE]  
    >  La visionneuse met en cache la liste initiale des règles, en fonction d'une requête portant sur le modèle d'exploration de données ; en outre, elle n'actualise pas la liste des règles tant que vous ne modifiez pas les conditions de la requête en définissant les lignes maximales, la probabilité, l'importance ou l'affichage des noms longs. Par conséquent, si vous tapez une condition et si l'affichage n'est pas immédiatement actualisé, vous pouvez forcer la visionneuse à actualiser les données en activant, puis en désactivant la case à cocher **Afficher le nom long** .  
  
### <a name="create-a-query-on-the-itemsets-in-an-association-model"></a>Créer une requête sur les jeux d'éléments dans un modèle d'association  
  
-   [Exemples de requêtes de modèle d’association](../../analysis-services/data-mining/association-model-query-examples.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Explorer un modèle à l'aide de la visionneuse de l'algorithme MAR (Microsoft Association Rules)](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)   
 [Leçon 3 : Génération d’un scénario de panier &#40;didacticiel d’exploration de données intermédiaire&#41;](http://msdn.microsoft.com/library/651eef38-772e-4d97-af51-075b1b27fc5a)  
  
  
