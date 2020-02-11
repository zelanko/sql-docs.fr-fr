---
title: BottomCount (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0bbd80998f7a6fd74f76f641cc16fe81ba715dde
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68889849"
---
# <a name="bottomcount-dmx"></a>BottomCount (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne le nombre spécifié de lignes les plus basses, dans l'ordre croissant, comme indiqué par une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BottomCount(<table expression>, <rank expression>, <count>)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Expression qui retourne une table, telle qu’une référence \<de colonne de table>, ou une fonction qui retourne une table.  
  
## <a name="return-type"></a>Type de retour  
 \<expression de table>  
  
## <a name="remarks"></a>Notes  
 La valeur fournie par l' \<expression de classement> argument détermine l’ordre croissant de classement des lignes fournies dans l' \<expression de table> argument, et le nombre de lignes les plus basses spécifiées dans l' \<argument Count> est retourné.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une requête de prédiction sur le modèle d’association que vous générez à l’aide du didacticiel sur l' [exploration de données de base](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
 Pour comprendre le fonctionnement de BottomCount, il peut être utile d’exécuter d’abord une requête de prédiction qui retourne uniquement la table imbriquée.  
  
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
  
 La fonction BottomCount prend les résultats de cette requête et retourne les lignes dont la valeur la plus petite somme au pourcentage spécifié.  
  
```  
SELECT   
BottomCount  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    3)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Le premier argument de la fonction BottomCount est le nom d’une colonne de table. Dans cet exemple, la table imbriquée est retournée en appelant la fonction Predict et en utilisant l’argument INCLUDE_STATISTICS.  
  
 Le deuxième argument de la fonction BottomCount est la colonne de la table imbriquée que vous utilisez pour classer les résultats. Dans cet exemple, l'option INCLUDE_STATISTICS retourne les colonnes $SUPPORT, $PROBABILTY et $ADJUSTED PROBABILITY. Cet exemple utilise $SUPPORT car les valeurs de support ne sont pas fractionnaires et sont donc plus faciles à vérifier.  
  
 Le troisième argument de la fonction BottomCount spécifie le nombre de lignes. Pour obtenir les trois lignes dont le niveau de classement est le plus bas, tel que classé par $SUPPORT, tapez 3.  
  
 Résultats de l’exemple :  
  
|Modèle|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Road Bottle Cage|1195|0,080314537|0,077173962|  
|Mountain Bottle Cage|1367|0,091874454|0,087780332|  
|Fender Set - Mountain|1415|0,095100477|0,090718432|  
  
 **Remarque** Cet exemple est fourni uniquement pour illustrer l’utilisation de BottomCount. L'exécution de cette requête peut prendre beaucoup de temps, en fonction de la taille de votre jeu de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;&#41;DMX](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [BottomPercent&#41;DMX &#40;](../dmx/bottompercent-dmx.md)   
 [BottomSum&#41;DMX &#40;](../dmx/bottomsum-dmx.md)   
 [&#40;DMX&#41;](../dmx/topcount-dmx.md)  
  
  
