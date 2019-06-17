---
title: PredictAssociation (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7a23407b546bcde2dd1fde81654da4fe861e0719
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62501835"
---
# <a name="predictassociation-dmx"></a>PredictAssociation (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Prévoit une appartenance associative.  
  
Par exemple, vous pouvez utiliser la fonction PredictAssociation pour obtenir l’ensemble des recommandations compte tenu de l’état actuel du panier d’achat pour un client. 
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PredictAssociation(<table column reference>, option1, option2, n ...)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Algorithmes qui contiennent des tables imbriquées prévisibles, y compris l’association et certains algorithmes de classification. Les algorithmes de classification qui prennent en charge des tables imbriquées sont le [!INCLUDE[msCoName](../includes/msconame-md.md)] arbres de décision, [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes, et [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithmes de réseau neuronal.  
  
## <a name="return-type"></a>Type de retour  
 \<expression de table >  
  
## <a name="remarks"></a>Notes  
 Les options pour le **PredictAssociation** fonction inclure EXCLUDE_NULL, INCLUDE_NULL, INCLUSIVE, EXCLUSIVE (par défaut), INPUT_ONLY, INCLUDE_STATISTICS et INCLUDE_NODE_ID.  
  
> [!NOTE]  
>  INCLUSIVE, EXCLUSIVE, INPUT_ONLY et INCLUDE_STATISTICS s'appliquent uniquement à une référence de colonne de table, et EXCLUDE_NULL et INCLUDE_NULL s'appliquent uniquement à une référence de colonne scalaire.  
  
 INCLUDE_STATISTICS retourne uniquement **$Probability** et **$AdjustedProbability**.  
  
 Si le paramètre numérique *n* est spécifié, le **PredictAssociation** fonction retourne les n premières valeurs probables selon la probabilité :  
  
```  
PredictAssociation(colref, [$AdjustedProbability], n)  
```  
  
 Si vous incluez **$AdjustedProbability**, l’instruction retourne la partie supérieure *n* valeurs basées sur les **$AdjustedProbability**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise le **PredictAssociation** fonction pour retourner les quatre produits de la société Adventure Works de base de données qui sont susceptibles d’être vendus ensemble.  
  
```  
SELECT  
  PredictAssociation([Association].[v Assoc Seq Line Items],4)  
From  
  [Association]  
```  
L’exemple suivant montre comment vous pouvez utiliser une table imbriquée comme entrée pour la fonction de prédiction, à l’aide de la clause de forme. La requête SHAPE crée un ensemble de lignes avec customerId comme une seule colonne et une table imbriquée en tant que deuxième colonne, qui contient la liste des produits, qu'un client a déjà apporté. 

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
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Functions &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
