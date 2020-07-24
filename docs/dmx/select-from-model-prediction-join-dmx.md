---
title: SELECT FROM &lt; Model &gt; PREDICTION JOIN (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e3e4e9a4d929d9533b10d87654f685e45dafd238
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970501"
---
# <a name="select-from-ltmodelgt-prediction-join-dmx"></a>SELECT FROM &lt; Model &gt; PREDICTION JOIN (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Utilise un modèle d'exploration de données pour prévoir les états des colonnes dans une source de données externe. L’instruction **PREDICTION JOIN** correspond à chaque cas de la requête source au modèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <select expression list>   
FROM <model> | <sub select> [NATURAL] PREDICTION JOIN   
<source data query> [ON <join mapping list>]   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 Optionnel. Entier qui spécifie le nombre de lignes à retourner.  
  
 *sélectionner la liste d’expressions*  
 Liste séparée par des virgules des identificateurs de colonnes et expressions dérivées du modèle d'exploration de données.  
  
 *model*  
 Identificateur du modèle  
  
 *sous-sélection*  
 Instruction Select incorporée  
  
 *requête de données sources*  
 Requête source  
  
 *liste de mappage de jointure*  
 Optionnel. Expression logique qui compare les colonnes du modèle aux colonnes de la requête source.  
  
 *expression de condition*  
 Optionnel. Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Optionnel. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 La clause ON définit le mappage entre les colonnes de la requête source et les colonnes du modèle d'exploration de données. Ce mappage sert à diriger les colonnes depuis la requête source vers les colonnes du modèle d'exploration de données de sorte que les colonnes puissent être utilisées en valeurs d'entrée pour créer des prédictions. Les colonnes du \<*join mapping list*> sont liées à l’aide d’un signe égal (=), comme indiqué dans l’exemple suivant :  
  
```  
[MiningModel].ColumnA = [source data query].Column1 AND   
[MiningModel].ColumnB = [source data query].Column2 AND  
...  
```  
  
 Si vous liez une table imbriquée dans la clause ON, veillez à lier la colonne clé avec des colonnes non clé de sorte que l'algorithme puisse identifier correctement à quel cas appartient l'enregistrement de la colonne imbriquée.  
  
 La requête source de la jointure de prévision peut être une table ou une requête singleton.  
  
 Vous pouvez spécifier des fonctions de prédiction qui ne retournent pas d’expression de table dans \<*select expression list*> et \<*condition expression*> .  
  
 La **jointure de prédiction naturelle** mappe automatiquement les noms de colonnes de la requête source qui correspondent aux noms de colonne dans le modèle. Si vous utilisez la **prédiction naturelle**, vous pouvez omettre la clause on.  
  
 La condition WHERE ne peut être appliquée qu'aux colonnes prédictibles ou associées.  
  
 La clause ORDER BY ne peut accepter qu'une seule colonne comme argument ; autrement dit, vous ne pouvez pas effectuer de tri sur plusieurs colonnes.  
  
## <a name="example-1-singleton-query"></a>Exemple 1 : requête singleton  
 L'exemple suivant montre comment créer une requête permettant de prédire si une personne spécifique achètera ou non une bicyclette en temps réel. Dans cette requête, les données ne sont pas stockées dans une table ou toute autre source de données, mais sont directement entrées dans la requête. La personne spécifiée dans la requête possède les caractéristiques suivantes :  
  
-   35 ans  
  
-   Propriétaire d'une maison  
  
-   Deux voitures  
  
-   Deux enfants à charge  
  
 À l’aide du modèle d’exploration de données arbre de décision TM et des caractéristiques connues sur le sujet, la requête retourne une valeur booléenne qui indique si la personne a acheté le vélo et un ensemble de valeurs tabulaires, retournées par la fonction [PredictHistogram &#40;DMX&#41;](../dmx/predicthistogram-dmx.md) , qui décrivent comment la prédiction a été effectuée.  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  PredictHistogram([Bike Buyer])  
FROM  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 35 AS [Age],  
  '5-10 Miles' AS [Commute Distance],  
  '1' AS [House Owner Flag],  
  2 AS [Number Cars Owned],  
  2 AS [Total Children]) AS t  
```  
  
## <a name="example-2-using-openquery"></a>Exemple 2 : utilisation de OPENQUERY  
 L'exemple suivant montre comment créer une requête de prédiction par lot à l'aide d'une liste de clients potentiels stockés dans un dataset externe. Étant donné que la table fait partie d’une vue de source de données qui a été définie sur une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , la requête peut utiliser [OPENQUERY](../dmx/source-data-query-openquery.md) pour récupérer les données. Étant donné que les noms des colonnes de la table sont différents de ceux du modèle d’exploration de données, la clause **on** doit être utilisée pour mapper les colonnes de la table aux colonnes du modèle.  
  
 La requête retourne le prénom et le nom de toutes les personnes de la table, ainsi qu'une colonne booléenne qui indique si chaque personne est susceptible d'acheter une bicyclette, où 0 signifie « n'achètera probablement pas de bicyclette » et 1 signifie « achètera probablement une bicyclette ». La dernière colonne contient la probabilité du résultat prédit.  
  
```  
SELECT  
  t.[LastName],  
  t.[FirstName],  
  [TM Decision Tree].[Bike Buyer],  
  PredictProbability([Bike Buyer])  
From  
  [TM Decision Tree]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT  
      [LastName],  
      [FirstName],  
      [MaritalStatus],  
      [Gender],  
      [YearlyIncome],  
      [TotalChildren],  
      [NumberChildrenAtHome],  
      [Education],  
      [Occupation],  
      [HouseOwnerFlag],  
      [NumberCarsOwned]  
    FROM  
      [dbo].[ProspectiveBuyer]  
    ') AS t  
ON  
  [TM Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
  [TM Decision Tree].[Gender] = t.[Gender] AND  
  [TM Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
  [TM Decision Tree].[Total Children] = t.[TotalChildren] AND  
  [TM Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
  [TM Decision Tree].[Education] = t.[Education] AND  
  [TM Decision Tree].[Occupation] = t.[Occupation] AND  
  [TM Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
  [TM Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
```  
  
 Pour restreindre le jeu de données uniquement aux clients prédits comme acheteurs de bicyclette, puis trier la liste par nom de client, vous pouvez ajouter une clause WHERE et une clause ORDER BY à l'exemple précédent :  
  
```  
WHERE [BIKE Buyer]  
ORDER BY [LastName] ASC  
```  
  
## <a name="example-3-predicting-associations"></a>Exemple 3 : prédiction des associations  
 L'exemple suivant montre comment créer une prévision en utilisant un modèle construit à partir de l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Association. Les prédictions sur un modèle d'association permettent de recommander des produits associés. Par exemple, la requête suivante retourne les trois produits qui ont le plus de chances d'être achetés ensemble :  
  
-   Mountain Bottle Cage  
  
-   Mountain Tire Tube  
  
-   Mountain-200  
  
 La fonction [Predict &#40;DMX&#41;](../dmx/predict-dmx.md) est polymorphe et peut être utilisée avec tous les types de modèles. Vous pouvez utiliser la valeur 3 comme argument pour la fonction afin de limiter le nombre d'articles retournés par la requête. La liste de **sélection** qui suit la clause NATURAL PREDICTION JOIN fournit les valeurs à utiliser comme entrée pour la prédiction.  
  
```  
SELECT FLATTENED  
  PREDICT([Association].[v Assoc Seq Line Items], 3)  
FROM  
  [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
  UNION SELECT 'Mountain Tire Tube' AS [Model]  
  UNION SELECT 'Mountain-200' AS [Model]) AS [v Assoc Seq Line Items ]) AS t  
```  
  
 Résultats de l'exemple :  
  
|Expression.Model|  
|----------------------|  
|HL Mountain Tire|  
|Water Bottle|  
|Fender Set - Mountain|  
  
 La colonne contenant l'attribut prédictible `[v Assoc Seq Line Items]` étant une colonne de table, la requête retourne une colonne unique qui contient une table imbriquée. Par défaut, la colonne de table imbriquée est appelée `Expression`. Si votre fournisseur ne prend pas en charge les ensembles de lignes hiérarchiques, vous pouvez utiliser le mot clé **aplati** comme indiqué dans cet exemple pour faciliter l’affichage des résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNER &#40;&#41;DMX](../dmx/select-dmx.md)   
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
