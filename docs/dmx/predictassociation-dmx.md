---
title: PredictAssociation (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a834c87c3febf0554ad07334000d62f1f9a93fee
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86968223"
---
# <a name="predictassociation-dmx"></a>PredictAssociation (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Prévoit une appartenance associative.  
  
Par exemple, vous pouvez utiliser la fonction PredictAssociation pour obtenir l’ensemble de recommandations en fonction de l’état actuel du panier d’achat d’un client. 
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PredictAssociation(<table column reference>, option1, option2, n ...)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Les algorithmes qui contiennent des tables imbriquées prévisibles, y compris l’Association et certains algorithmes de classification. Les algorithmes de classification qui prennent en charge les tables imbriquées incluent les [!INCLUDE[msCoName](../includes/msconame-md.md)] arbres de décision, les [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes et les [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithmes de réseau neuronal.  
  
## <a name="return-type"></a>Type de retour  
 \<table expression>  
  
## <a name="remarks"></a>Notes  
 Les options de la fonction **PredictAssociation** sont EXCLUDE_NULL, INCLUDE_NULL, inclusives, exclusives (par défaut), INPUT_ONLY, INCLUDE_STATISTICS et INCLUDE_NODE_ID.  
  
> [!NOTE]  
>  INCLUSIVE, EXCLUSIVE, INPUT_ONLY et INCLUDE_STATISTICS s'appliquent uniquement à une référence de colonne de table, et EXCLUDE_NULL et INCLUDE_NULL s'appliquent uniquement à une référence de colonne scalaire.  
  
 INCLUDE_STATISTICS retourne uniquement **$Probability** et **$AdjustedProbability**.  
  
 Si le paramètre numérique *n* est spécifié, la fonction **PredictAssociation** retourne les n premières valeurs les plus probables en fonction de la probabilité :  
  
```  
PredictAssociation(colref, [$AdjustedProbability], n)  
```  
  
 Si vous incluez **$AdjustedProbability**, l’instruction retourne les *n* premières valeurs en fonction du **$AdjustedProbability**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise la fonction **PredictAssociation** pour retourner les quatre produits de la base de données Adventure Works qui sont le plus susceptibles d’être vendus ensemble.  
  
```  
SELECT  
  PredictAssociation([Association].[v Assoc Seq Line Items],4)  
From  
  [Association]  
```  
L’exemple suivant montre comment vous pouvez utiliser une table imbriquée comme entrée de la fonction de prédiction à l’aide de la clause SHAPE. La requête SHAPE crée un ensemble de lignes avec customerId comme une colonne et une table imbriquée sous la forme d’une deuxième colonne, qui contient la liste des produits déjà importés par un client. 

~~~~
SELECT T.[CustomerId], PredictAssociation(MyNestedTable, 5) // returns top 5 associated items
FROM My Model
PREDICTION JOIN
SHAPE {
    OPENQUERY([Adventure Works DW],'SELECT CustomerID, OrderNumber
    FROM vAssocSeqOrders ORDER BY OrderNumber')
} APPEND (
    {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, model FROM 
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}
  RELATE OrderNumber to OrderNumber) AS T
~~~~  

  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40;&#41;DMX](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)  
  
  
