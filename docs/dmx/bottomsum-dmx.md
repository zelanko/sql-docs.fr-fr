---
description: BottomSum (DMX)
title: BottomSum (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 551fde90989093ab601cfa6100b6c6e208fac9e6
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727743"
---
# <a name="bottomsum-dmx"></a>BottomSum (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Retourne, dans l'ordre croissant, les lignes les plus basses d'une table dont le total cumulé est au moins égal à une valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BottomSum(<table expression>, <rank expression>, <sum>)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Expression qui retourne une table, telle qu’un \<table column reference> , ou une fonction qui retourne une table.  
  
## <a name="return-type"></a>Type de retour  
 \<table expression>  
  
## <a name="remarks"></a>Notes  
 La fonction **BottomSum** retourne les lignes les plus basses dans l’ordre croissant de classement. Le classement est basé sur la valeur évaluée de l' \<rank expression> argument pour chaque ligne, de telle sorte que la somme des \<rank expression> valeurs soit au moins égale au total spécifié par l' \<sum> argument. **BottomSum** retourne le plus petit nombre d’éléments possible tout en continuant à répondre à la valeur de somme spécifiée.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une requête de prédiction sur le modèle d’association que vous générez à l’aide du didacticiel sur l' [exploration de données de base](/previous-versions/sql/sql-server-2016/ms167167(v=sql.130)).  
  
 Pour comprendre le fonctionnement de BottomSum, il peut être utile d’exécuter d’abord une requête de prédiction qui retourne uniquement la table imbriquée.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  Dans cet exemple, la valeur fournie en tant qu'entrée contient un guillemet simple et doit donc être placée dans une séquence d'échappement en la préfaçant avec un autre guillemet simple. Si vous n'êtes pas certain de la syntaxe permettant d'insérer un caractère d'échappement, vous pouvez utiliser le Générateur de requêtes de prédiction pour créer la requête. Lorsque vous sélectionnez la valeur dans la liste déroulante, le caractère d'échappement requis est inséré pour vous. Pour plus d’informations, consultez [créer une requête singleton dans le concepteur d’exploration de données](/analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer).  
  
 Résultats de l'exemple :  
  
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
  
 La fonction BottomSum prend les résultats de cette requête et retourne les lignes avec les valeurs les plus basses qui totalisent le nombre spécifié.  
  
```  
SELECT   
BottomSum  
    (  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $PROBABILITY,  
    .1)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Le premier argument de la fonction BottomSum est le nom d’une colonne de table. Dans cet exemple, la table imbriquée est retournée en appelant la fonction Predict et en utilisant l’argument INCLUDE_STATISTICS.  
  
 Le deuxième argument de la fonction BottomSum est la colonne de la table imbriquée que vous utilisez pour classer les résultats. Dans cet exemple, l'option INCLUDE_STATISTICS retourne les colonnes $SUPPORT, $PROBABILTY et $ADJUSTED PROBABILITY. Cet exemple utilise $PROBABILITY pour retourner les lignes dont la somme est au moins égale à une probabilité de 50 %.  
  
 Le troisième argument de la fonction BottomSum spécifie la somme cible, sous la forme d’un double. Pour obtenir les lignes pour les produits à nombre le plus bas dont la somme est égale à une probabilité de 10 pour cent, tapez .1.  
  
 Résultats de l'exemple :  
  
|Modèle|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Road Bottle Cage|1195|0,08...|0,07...|  
|Mountain Bottle Cage|1367|0,09...|0,08...|  
  
 **Remarque** Cet exemple est fourni uniquement pour illustrer l’utilisation de BottomSum. L'exécution de cette requête peut prendre beaucoup de temps, en fonction de la taille de votre jeu de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;&#41;DMX ](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX ](../dmx/general-prediction-functions-dmx.md)   
 [BottomPercent&#41;DMX &#40;](../dmx/bottompercent-dmx.md)  
  
