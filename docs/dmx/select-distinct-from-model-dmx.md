---
title: SELECT DISTINCT FROM &lt; Model &gt; (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ea538271bf84d7d5b4e0fbea0a860f68bb1f62b6
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669620"
---
# <a name="select-distinct-from-ltmodel-gt-dmx"></a>SELECT DISTINCT FROM &lt; Model &gt; (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne tous les états possibles de la colonne sélectionnée dans le modèle. Les valeurs qui sont retournées varient selon que la colonne spécifiée contient des valeurs discrètes, des valeurs numériques discrétisées ou des valeurs numériques continues.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [FLATTENED] DISTINCT [TOP <n>] <expression list> FROM <model>   
[WHERE <condition list>][ORDER BY <expression>]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 facultatif. Entier spécifiant le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste séparée par des virgules des identificateurs des colonnes associées (dérivées du modèle) ou expressions.  
  
 *model*  
 Identificateur du modèle  
  
 *liste de conditions*  
 Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 L’instruction **Select distinct from** ne fonctionne qu’avec une seule colonne ou avec un ensemble de colonnes associées. Cette clause ne fonctionne pas avec un ensemble de colonnes non associées.  
  
 L’instruction **Select distinct from** vous permet de référencer directement une colonne à l’intérieur d’une table imbriquée. Par exemple :  
  
```  
<model>.<table column reference>.<column reference>  
```  
  
 Les résultats de l’instruction **Select distinct from \< Model>** varient en fonction du type de colonne. Le tableau ci-dessous décrit les types de colonnes pris en charge et le résultat de l'instruction.  
  
|Type de colonne|Output|  
|-----------------|------------|  
|Discret|Valeurs uniques de la colonne|  
|Discrétisé|Point milieu de chaque compartiment discrétisé de la colonne.|  
|Continue|Point milieu des valeurs de la colonne|  
  
## <a name="discrete-column-example"></a>Exemple de colonne discrète  
 L’exemple de code suivant est basé sur le `[TM Decision Tree]` modèle que vous créez dans le didacticiel sur l' [exploration de données de base](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). La requête retourne les valeurs uniques qui existent dans la colonne discrète `Gender`.  
  
```  
SELECT DISTINCT [Gender]  
FROM [TM Decision Tree]  
```  
  
 Résultats de l'exemple :  
  
|Sexe|  
|------------|  
||  
|F|  
|M|  
  
 Pour les colonnes qui contiennent des valeurs discrètes, les résultats incluent systématiquement l'état Missing, présenté comme une valeur Null.  
  
## <a name="continuous-column-example"></a>Exemple de colonne continue  
 L'exemple de code suivant retourne le point milieu, l'âge minimal et l'âge maximal de toutes les valeurs de la colonne.  
  
```  
SELECT DISTINCT [Age] AS [Midpoint Age],   
    RangeMin([Age]) AS [Minimum Age],   
    RangeMax([Age]) AS [Maximum Age]  
FROM [TM Decision Tree]  
```  
  
 Résultats de l'exemple :  
  
|Midpoint Age|Minimum Age|Maximum Age|  
|------------------|-----------------|-----------------|  
||||  
|62|26|97|  
  
 La requête retourne également une ligne unique de valeurs Null, pour représenter les valeurs manquantes.  
  
## <a name="discretized-column-example"></a>Exemple de colonne discrétisée.  
 L'exemple de code suivant retourne le point milieu et les valeurs maximales et minimales de chaque compartiment créé par l'algorithme pour la colonne, [`Yearly Income]`. Pour reproduire les résultats de cet exemple, vous devez créer une nouvelle structure d'exploration de données identique à `[Targeted Mailing]`. Dans l’Assistant, modifiez le type de contenu de la `Yearly Income` colonne de **continue** en **discrétisation**.  
  
> [!NOTE]  
>  Vous pouvez également modifier le modèle d'exploration de données créé dans le Didacticiel sur l'exploration de données de base afin de discrétiser la colonne de structure d'exploration de données, [`Yearly Income]`. Pour plus d’informations sur la façon de procéder, consultez [modifier la discrétisation d’une colonne dans un modèle d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model). Toutefois, le fait de modifier le discrétisation de la colonne force le retraitement de la structure d'exploration de données et modifie les résultats des autres modèles créés à l'aide de cette structure.  
  
```  
SELECT DISTINCT [Yearly Income] AS [Bucket Average],   
    RangeMin([Yearly Income]) AS [Bucket Minimum],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
 Résultats de l'exemple :  
  
|Bucket Average|Bucket Minimum|Bucket Maximum|  
|--------------------|--------------------|--------------------|  
||||  
|24610,7|10000|39221,41|  
|55115,73|39221,41|71010,05|  
|84821,54|71010,05|98633,04|  
|111633,9|98633,04|124634,7|  
|147317,4|124634,7|170000|  
  
 Vous constatez que les valeurs de la colonne [Yearly Income] ont été discrétisées dans cinq compartiments, plus une ligne supplémentaire de valeurs Null pour représenter les valeurs manquantes.  
  
 Le nombre de décimales dans les résultats dépend du client utilisé pour l'interrogation. Dans cet exemple, ils ont été arrondis à deux décimales, à la fois pour des raisons de simplicité et pour refléter les valeurs affichées dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 Par exemple, si vous parcourez le modèle en utilisant la Visionneuse d'arbre de décision et que vous cliquez sur un nœud qui contient des clients regroupés par revenu, les propriétés de nœud suivantes s'affichent dans l'info-bulle :  
  
 Âge >= 69 et revenus annuels < 39221,41  
  
> [!NOTE]  
>  La valeur minimale du compartiment minimal et la valeur maximale du compartiment maximal correspondent aux valeurs observées la plus élevée et la moins élevée. Les valeurs hors de cette plage observée sont supposées appartenir aux compartiments minimaux et maximaux.  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNER &#40;&#41;DMX](../dmx/select-dmx.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
