---
title: Prédiction (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eb939c45d298117fa81b05d6188aa3a4c5cd7c4b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68008157"
---
# <a name="predict-dmx"></a>Predict (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  La fonction **Predict** retourne une valeur prédite, ou un ensemble de valeurs, pour une colonne spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Predict(<scalar column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
Predict(<table column reference>, [option1], [option2], [option n], [INCLUDE_NODE_ID], n)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Référence de colonne scalaire ou référence de colonne de table.  
  
## <a name="return-type"></a>Type de retour  
 \<> de référence de colonne scalaire  
  
 or  
  
 \<> de référence de colonne de table  
  
 Le type de retour dépend du type de colonne auquel cette fonction est appliquée.  
  
> [!NOTE]  
>  INCLUSIVE, EXCLUSIVE, INPUT_ONLY et INCLUDE_STATISTICS s'appliquent uniquement à une référence de colonne de table, et EXCLUDE_NULL et INCLUDE_NULL s'appliquent uniquement à une référence de colonne scalaire.  
  
## <a name="remarks"></a>Notes  
 Les options sont EXCLUDE_NULL (par défaut), INCLUDE_NULL, INCLUSIVE, EXCLUSIVE (par défaut), INPUT_ONLY et INCLUDE_STATISTICS.  
  
> [!NOTE]  
>  Pour les modèles de série chronologique, la fonction Predict ne prend pas en charge INCLUDE_STATISTICS.  
  
 Le paramètre INCLUDE_NODE_ID retourne la colonne $NODEID dans le résultat. NODE_ID est le nœud de contenu sur lequel la prédiction est exécutée pour un cas particulier. Ce paramètre est facultatif lors de l’utilisation de Predict sur des colonnes de table.  
  
 Le paramètre *n* s’applique aux colonnes de table. Il définit le nombre de lignes retournées en fonction du type de prédiction. Si la colonne sous-jacente est Sequence, elle appelle la fonction **PredictSequence** . Si la colonne sous-jacente est une série chronologique, elle appelle la fonction **PredictTimeSeries** . Pour les types associatifs de prédiction, elle appelle la fonction **PredictAssociation** .  
  
 La fonction **Predict** prend en charge le polymorphisme.  
  
 Les formes abrégées des autres solutions suivantes sont fréquemment utilisées :  
  
-   [Sexe] est une alternative à la **prédiction**([sexe], EXCLUDE_NULL).  
  
-   [Products Purchases] est une alternative à **Predict**([Products Purchases], EXCLUDE_NULL, exclusive).  
  
    > [!NOTE]  
    >  Le type de retour de cette fonction est lui-même considéré comme une référence de colonne. Cela signifie que la fonction **Predict** peut être utilisée comme argument dans d’autres fonctions qui prennent une référence de colonne comme argument (à l’exception de la fonction **Predict** elle-même).  
  
 Le passage d’INCLUDE_STATISTICS à une prédiction sur une colonne à valeur de table ajoute les colonnes **$Probability** et **$support** à la table résultante. Ces colonnes décrivent la probabilité de l'existence de l'enregistrement de table imbriquée associée.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise la fonction Predict pour retourner les quatre produits de la base de données Adventure Works qui sont le plus susceptibles d’être vendus ensemble. Étant donné que la fonction est prédite par rapport à un modèle d’exploration de données de règles d’association, elle utilise automatiquement la fonction **PredictAssociation** comme décrit précédemment.  
  
```  
SELECT  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,4)  
FROM     [Association]  
```  
  
 Exemples de résultats :  
  
 Cette requête retourne une ligne de données unique à une colonne (`Expression`) qui contient la table imbriquée suivante.  
  
|Modèle|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016331743|0.252695851192499|  
|Water Bottle|2866|0.192620471805901|0.175205052318795|  
|Patch Kit|2113|0.142012232004839|0.132389356196586|  
|Mountain Tire Tube|1992|0.133879965051415|0.125304947722259|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40;&#41;DMX](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)  
  
  
