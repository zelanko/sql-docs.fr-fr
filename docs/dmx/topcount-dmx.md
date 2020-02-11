---
title: Nombre de points (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d4b91b06470c9cb22e98ac76ea52494728a7ca11
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68893107"
---
# <a name="topcount-dmx"></a>TopCount (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne le nombre spécifié de lignes les plus hautes dans l'ordre décroissant, comme indiqué par une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TopCount(<table expression>, <rank expression>, <count>)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Expression qui retourne une table, telle qu’une référence \<de colonne de table>, ou une fonction qui retourne une table.  
  
## <a name="return-type"></a>Type de retour  
 \<expression de table>  
  
## <a name="remarks"></a>Notes  
 La valeur fournie par l' \<expression de classement> argument détermine l’ordre de classement décroissant des lignes fournies dans l' \<expression de table> argument, et le nombre de lignes supérieures spécifié dans l' \<argument Count> est retourné.  
  
 La fonction TopCount a été introduite à l’origine pour activer les prédictions associatives et, en général, produit les mêmes résultats qu’une instruction qui comprend des clauses **SELECT TOP** et **order by** . Vous obtiendrez de meilleures performances pour les prédictions associatives si vous utilisez la fonction **Predict (DMX)** , qui prend en charge la spécification d’un certain nombre de prédictions à retourner.  
  
 Toutefois, dans certaines situations, il se peut que vous deviez toujours utiliser le nombre de la valeur. Par exemple, DMX ne prend pas en charge le qualificateur **Top** dans une instruction sub-select. La fonction [PredictHistogram &#40;DMX&#41;](../dmx/predicthistogram-dmx.md) ne prend pas non plus en charge l’ajout de **Top**.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants sont des requêtes de prédiction sur le modèle d’association que vous générez à l’aide du didacticiel sur l' [exploration de données de base](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Les requêtes retournent les mêmes résultats, mais le premier exemple utilise la fonction TopCount, tandis que le deuxième exemple utilise la fonction Predict.  
  
 Pour comprendre le fonctionnement de la fonction TopCount, il peut être utile d’exécuter d’abord une requête de prédiction qui retourne uniquement la table imbriquée.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  Dans cet exemple, la valeur fournie en tant qu'entrée contient un guillemet simple et doit donc être placée dans une séquence d'échappement en la préfaçant avec un autre guillemet simple. Si vous n'êtes pas certain de la syntaxe permettant d'insérer un caractère d'échappement, vous pouvez utiliser le Générateur de requêtes de prédiction pour créer la requête. Lorsque vous sélectionnez la valeur dans la liste déroulante, le caractère d'échappement requis est inséré pour vous. Pour plus d’informations, consultez [créer une requête singleton dans le concepteur d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer).  
  
 Résultats de l’exemple :  
  
|Modèle|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0,291283016|0,252695851|  
|Water Bottle|2866|0,192620472|0,175205052|  
|Patch kit|2113|0,142012232|0,132389356|  
|Mountain Tire Tube|1992|0,133879965|0,125304948|  
|Mountain-200|1755|0,117951475|0,111260823|  
|Road Tire Tube|1588|0,106727603|0,101229538|  
|Cycling Cap|1473|0,098998589|0,094256014|  
|Fender Set - Mountain|1415|0,095100477|0,090718432|  
|Mountain Bottle Cage|1367|0,091874454|0,087780332|  
|Road Bottle Cage|1195|0,080314537|0,077173962|  
  
 La fonction TopCount prend les résultats de cette requête et retourne le nombre spécifié de lignes dont la valeur est la plus petite.  
  
```  
SELECT   
TopCount  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    3)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Le premier argument de la fonction TopCount est le nom d’une colonne de table. Dans cet exemple, la table imbriquée est retournée en appelant la fonction Predict et en utilisant l’argument INCLUDE_STATISTICS.  
  
 Le deuxième argument de la fonction TopCount est la colonne de la table imbriquée que vous utilisez pour classer les résultats. Dans cet exemple, l'option INCLUDE_STATISTICS retourne les colonnes $SUPPORT, $PROBABILTY et $ADJUSTED PROBABILITY. Cet exemple utilise $SUPPORT pour classer les résultats.  
  
 Le troisième argument de la fonction TopCount spécifie le nombre de lignes à retourner, sous la forme d’un entier. Pour obtenir les trois produits supérieurs, tel que classé par $SUPPORT, tapez 3.  
  
 Résultats de l’exemple :  
  
|Modèle|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0,29...|0,25...|  
|Water Bottle|2866|0,19...|0,17...|  
|Patch kit|2113|0,14...|0,13...|  
  
 Toutefois, ce type de requête peut affecter les performances dans un environnement de production. Cela est dû au fait que la requête retourne un ensemble de toutes les prédictions de l'algorithme, trie ces prédictions et retourne les 3 prédictions supérieures.  
  
 L'exemple suivant fournit une autre instruction qui retourne les mêmes résultats mais s'exécute beaucoup plus rapidement. Cet exemple remplace la fonction TopCount par la fonction Predict, qui accepte un certain nombre de prédictions en tant qu’argument. Cet exemple utilise également le mot clé **$support** pour récupérer directement la colonne de table imbriquée.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3, $SUPPORT)  
```  
  
 Les résultats contiennent les 3 prédictions supérieures triées par la valeur de support. Vous pouvez remplacer $SUPPORT par $PROBABILITY ou $ADJUSTED_PROBABILITY pour retourner des prédictions classées par probabilité ou par probabilité ajustée. Pour plus d’informations, voir **Predict (DMX)**.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;&#41;DMX](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)   
 [&#41;DMX &#40;](../dmx/toppercent-dmx.md)   
 [&#41;DMX &#40;DMX](../dmx/topsum-dmx.md)  
  
  
