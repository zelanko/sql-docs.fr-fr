---
description: PredictTimeSeries (DMX)
title: PredictTimeSeries (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 13655aadf5f95b776b83e48791e4f423d6ccc355
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422262"
---
# <a name="predicttimeseries-dmx"></a>PredictTimeSeries (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Retourne les valeurs suivantes prédites pour les données de série chronologique. Les données de séries chronologiques étant continues, elles peuvent être stockées dans une table imbriquée ou une table de cas. La fonction **PredictTimeSeries** retourne toujours une table imbriquée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PredictTimeSeries(<table column reference>)  
PredictTimeSeries(<table column reference>, n)  
PredictTimeSeries(<table column reference>, n-start, n-end)  
PredictTimeSeries(<scalar column reference>)  
PredictTimeSeries(<scalar column reference>, n)  
PredictTimeSeries(<scalar column reference>, n-start, n-end)  
PredictTimeSeries(<table column reference>, n, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
PredictTimeSeries(<table column reference>, n-start, n-end, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
PredictTimeSeries(<scalar column reference>, n, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
PredictTimeSeries(<scalar column reference>, n-start, n-end, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
```  
  
## <a name="arguments"></a>Arguments  
 *\<table column reference>*, *\<scalar column referenc>*  
 Spécifie le nom de la colonne à prédire. La colonne peut contenir des données scalaires ou tabulaires.  
  
 *n*  
 Spécifie le nombre d'étapes suivantes à prédire. Si aucune valeur n’est spécifiée pour *n*, la valeur par défaut est 1.  
  
 *n* ne peut pas être égal à 0. La fonction retourne une erreur si vous ne faites pas au moins une prédiction.  
  
 *n-Start, n-end*  
 Spécifie une plage d'étapes de série chronologique.  
  
 *n-Start* doit être un entier et ne peut pas être égal à 0.  
  
 *n-end* doit être un entier supérieur à *n-Start*.  
  
 *\<source query>*  
 Définit les données externes qui sont utilisées pour faire des prédictions.  
  
 REPLACE_MODEL_CASES | EXTEND_MODEL_CASES  
 Indique comment gérer de nouvelles données.  
  
 REPLACE_MODEL_CASES spécifie que les points de données dans le modèle doivent être remplacés par les nouvelles données. Toutefois, les prédictions sont basées sur les modèles dans le modèle d'exploration de données existant.  
  
 EXTEND_MODEL_CASES spécifie que les nouvelles données doivent être ajoutées au jeu de données d'apprentissage d'origine. Les futures prédictions sont élaborées uniquement sur le jeu de données composite après que les nouvelles données ont été utilisées.  
  
 Ces arguments peuvent être uniquement utilisés lorsque les nouvelles données sont ajoutées à l'aide d'une instruction PREDICTION JOIN. Si vous utilisez une requête PREDICTION JOIN et que vous ne spécifiez pas d'argument, la valeur par défaut est EXTEND_MODEL_CASES.  
  
## <a name="return-type"></a>Type de retour  
 \<*table expression*>  
  
## <a name="remarks"></a>Notes  
 L'algorithme MTS ([!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series) ne prend pas en charge la prédiction historique lorsque vous utilisez l'instruction PREDICTION JOIN pour ajouter de nouvelles données.  
  
 Dans une instruction PREDICTION JOIN, le processus de prédiction commence toujours à l'étape venant immédiatement après la fin de la série d'apprentissage d'origine. Cela est vrai même si vous ajoutez de nouvelles données. Par conséquent, le paramètre *n* et les valeurs de paramètre *n-Start* doivent être un entier supérieur à 0.  
  
> [!NOTE]  
>  La longueur des nouvelles données n'affecte pas le point de départ de la prédiction. Par conséquent, si vous souhaitez ajouter de nouvelles données et faire de nouvelles prédictions, assurez-vous soit d'attribuer au point de départ de prédiction une valeur supérieure à la longueur des nouvelles données, soit d'étendre le point de fin de prédiction de la durée des nouvelles données.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants montrent comment faire des prédictions sur un modèle de série chronologique existant :  
  
-   Le premier exemple montre comment faire un nombre spécifié de prédictions basées sur le modèle actif.  
  
-   Le deuxième exemple indique comment utiliser le paramètre REPLACE_MODEL_CASES pour appliquer les modèles dans le modèle spécifié à un nouveau jeu de données.  
  
-   Le troisième exemple indique comment utiliser le paramètre EXTEND_MODEL_CASES pour mettre à jour un modèle d'exploration de données avec de nouvelles données.  
  
 Pour en savoir plus sur l’utilisation des modèles de séries chronologiques, consultez le didacticiel sur l’exploration de données, [leçon 2 : génération d’un scénario de prévision &#40;exploration intermédiaire de l’exploration de données&#41;](https://msdn.microsoft.com/library/9a988156-c900-4c22-97fa-f6b0c1aea9e2) et le [didacticiel DMX sur la prédiction de série chronologique](https://msdn.microsoft.com/library/38ea7c03-4754-4e71-896a-f68cc2c98ce2).  
  
> [!NOTE]  
>  Vous pouvez obtenir des résultats différents de votre modèle ; les résultats des exemples suivants sont fournis uniquement pour illustrer le format de résultat.  
  
### <a name="example-1-predicting-a-number-of-time-slices"></a>Exemple 1 : Prédiction de plusieurs tranches de temps  
 L’exemple suivant utilise la fonction **PredictTimeSeries** pour retourner une prédiction pour les trois étapes suivantes, et limite les résultats à la série M200 dans les régions Europe et Pacifique. Dans ce modèle particulier, l’attribut prévisible est Quantity. vous devez donc utiliser `[Quantity]` comme premier argument de la fonction PredictTimeSeries.  
  
```  
SELECT FLATTENED  
    [Forecasting].[Model Region],  
    PredictTimeSeries([Forecasting].[Quantity],3)AS t   
FROM  
    [Forecasting]  
WHERE [Model Region] = 'M200 Europe'  
OR [Model Region] = 'M200 Pacific'  
```  
  
 Résultats attendus :  
  
|Model Region|t.$TIME|t.Quantity|  
|------------------|-------------|----------------|  
|M200 Europe|7/25/2008 12:00:00|121|  
|M200 Europe|8/25/2008 12:00:00|142|  
|M200 Europe|9/25/2008 12:00:00|152|  
|M200 Pacific|7/25/2008 12:00:00|46|  
|M200 Pacific|8/25/2008 12:00:00|44|  
|M200 Pacific|9/25/2008 12:00:00|42|  
  
 Dans cet exemple, le mot clé FLATTENED a été utilisé pour simplifier la lecture des résultats.  Si vous n'utilisez pas le mot clé FLATTENED et qu'à la place vous retournez un ensemble de lignes hiérarchique, cette requête retourne deux colonnes. La première contient la valeur de [ModelRegion] et la deuxième une table imbriquée à deux colonnes : $TIME, qui affiche les tranches de temps prédites, et Quantity, qui contient les valeurs prédites.  
  
### <a name="example-2-adding-new-data-and-using-replace_model_cases"></a>Exemple 2 : ajout de nouvelles données et utilisation de REPLACE_MODEL_CASES  
 Supposez que vous constatez que les données étaient incorrectes pour une région particulière et que vous souhaitez utiliser les modèles dans le modèle, tout en ajustant les prédictions pour qu'elles correspondent aux nouvelles données. Ou il se peut que vous constatiez qu'une autre région a des tendances plus fiables et que vous souhaitiez appliquer le modèle le plus fiable aux données d'une région différente.  
  
 Dans de tels scénarios, vous pouvez utiliser le paramètre REPLACE_MODEL_CASES et spécifier un nouveau jeu de données à utiliser comme données d'historique. De cette façon, les projections seront basées sur les modèles dans le modèle spécifié, mais continueront de manière fluide à partir de la fin des nouveaux points de données. Pour une procédure pas à pas complète de ce scénario, consultez [prédictions de série chronologique avancées &#40;didacticiel sur l’exploration de données intermédiaire&#41;](https://msdn.microsoft.com/library/b614ebdb-07ca-44af-a0ff-893364bd4b71).  
  
 La requête PREDICTION JOIN suivante illustre la syntaxe pour remplacer des données et élaborer de nouvelles prédictions. Pour les données de remplacement, l'exemple extrait la valeur des colonnes Amount et Quantity et multiplie chacune par deux :  
  
```  
SELECT [Forecasting].[Model Region],  
    PredictTimeSeries([Forecasting].[Quantity], 3, REPLACE_MODEL_CASES)   
FROM  
    [Forecasting]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT [ModelRegion],   
    ([Quantity] * 2) as Quantity,  
    ([Amount] * 2) as Amount,  
      [ReportingDate]  
    FROM [dbo].vTimeSeries  
    WHERE ModelRegion = N''M200 Pacific''  
    ') AS t  
ON  
  [Forecasting].[Model Region] = t.[ Model Region] AND  
[Forecasting].[Reporting Date] = t.[ReportingDate] AND  
[Forecasting].[Quantity] = t.[Quantity] AND  
[Forecasting].[Amount] = t.[Amount]  
```  
  
 Les tableaux suivants comparent les résultats de la prédiction.  
  
 Prédictions d’origine :  
  
|Model Region|ReportingDate|Quantité|  
|-|-|-|  
|M200 Pacific|7/25/2008 12:00:00|46|  
|M200 Pacific|8/25/2008 12:00:00|44|  
|M200 Pacific|9/25/2008 12:00:00|42|  
  
 Prédictions mises à jour :  
  
|Model Region|ReportingDate|Quantité|  
|-|-|-|  
|M200 Pacific|7/25/2008 12:00:00|91|  
|M200 Pacific|8/25/2008 12:00:00|89|  
|M200 Pacific|9/25/2008 12:00:00|84|  
  
### <a name="example-3-adding-new-data-and-using-extend_model_cases"></a>Exemple 3 : ajout de nouvelles données et utilisation d'EXTEND_MODEL_CASES  
 L’exemple 3 illustre l’utilisation de l’option *EXTEND_MODEL_CASES* pour fournir de nouvelles données, qui sont ajoutées à la fin d’une série de données existante. Plutôt que de remplacer les points de données existants, les nouvelles données sont ajoutées au modèle.  
  
 Dans l'exemple suivant, les nouvelles données sont fournies dans l'instruction SELECT qui suit NATURAL PREDICTION JOIN. Vous pouvez fournir plusieurs lignes de nouvelle entrée avec cette syntaxe, mais chaque nouvelle ligne d'entrée doit avoir un horodatage unique :  
  
```  
SELECT [Model Region],  
    PredictTimeSeries([Forecasting].[Quantity], 5, EXTEND_MODEL_CASES)   
FROM  
    [Forecasting]  
NATURAL PREDICTION JOIN  
    (SELECT  
        1 as [Reporting Date],  
        10 as [Quantity],  
        'M200 Europe' AS [Model Region]  
    UNION SELECT   
        2 as [Reporting Date],  
        15 as [Quantity],  
        'M200 Europe' AS [Model Region]  
) AS T  
WHERE ([Model Region] = 'M200 Europe'  
 OR [Model Region] = 'M200 Pacific')  
```  
  
 Étant donné que la requête utilise l’option *EXTEND_MODEL_CASES* , [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] effectue les actions suivantes pour ses prédictions :  
  
-   Augmente la taille totale des cas d'apprentissage en ajoutant les deux nouveaux mois de données au modèle.  
  
-   Démarre les prédictions à la fin des données de cas précédentes. Par conséquent, les deux premières prédictions représentent les nouveaux chiffres de ventes réels que vous venez d'ajouter au modèle.  
  
-   Retourne de nouvelles prédictions pour les trois tranches de temps restantes selon le modèle nouvellement développé.  
  
 Le tableau suivant répertorie les résultats de la requête de l'exemple 2. Remarquez que les deux premières valeurs retournées pour M200 Europe sont exactement les mêmes que les nouvelles valeurs que vous avez fournies. Ce comportement est inhérent à la conception ; si vous souhaitez démarrer des prédictions après la fin des nouvelles données, vous devez spécifier des étapes de début et de fin.  
  
 Notez également que vous n'avez pas fourni de nouvelles données pour la région Pacifique. Par conséquent, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] retourne de nouvelles prédictions pour les cinq tranches de temps.  
  
 Quantité : M200 Europe. EXTEND_MODEL_CASES :  
  
|$TIME|Quantité|  
|-----------|--------------|  
|7/25/2008 0:00|10|  
|8/25/2008 0:00|15|  
|9/25/2008 0:00|72|  
|10/25/2008 0:00|69|  
|11/25/2008 0:00|68|  
  
 Quantité : M200 Pacific. EXTEND_MODEL_CASES :  
  
|$TIME|Quantité|  
|-----------|--------------|  
|7/25/2008 0:00|46|  
|8/25/2008 0:00|44|  
|9/25/2008 0:00|42|  
|10/25/2008 0:00|42|  
|11/25/2008 0:00|38|  
  
## <a name="example-4-returning-statistics-in-a-time-series-prediction"></a>Exemple 4 : retour de statistiques dans une prédiction de série chronologique  
 La fonction **PredictTimeSeries** ne prend pas en charge *INCLUDE_STATISTICS* en tant que paramètre. Toutefois, la requête suivante peut être utilisée pour retourner les statistiques de prédiction pour une requête de série chronologique. Cette approche peut également être suivie avec des modèles qui ont des colonnes de tables imbriquées.  
  
 Dans ce modèle particulier, l’attribut prévisible est Quantity. vous devez donc utiliser `[Quantity]` comme premier argument de la fonction PredictTimeSeries. Si votre modèle utilise un autre attribut prédictible, vous pouvez substituer un nom de colonne différent.  
  
```  
SELECT FLATTENED [Model Region],  
(SELECT   
     $Time,  
     [Quantity] as [PREDICTION],   
     PredictVariance([Quantity]) AS [VARIANCE],  
     PredictStdev([Quantity]) AS [STDEV]  
FROM  
      PredictTimeSeries([Quantity], 3) AS t  
) AS t  
FROM Forecasting  
WHERE [Model Region] = 'M200 Europe'  
OR [Model Region] = 'M200 North America'  
```  
  
 Exemples de résultats :  
  
|Model Region|t.$TIME|t.PREDICTION|t.VARIANCE|t.STDEV|  
|------------------|-------------|------------------|----------------|-------------|  
|M200 Europe|7/25/2008 12:00:00|121|11.6050581415597|3.40661975300439|  
|M200 Europe|8/25/2008 12:00:00|142|10.678201866621|3.26775180615374|  
|M200 Europe|9/25/2008 12:00:00|152|9.86897842568614|3.14149302493037|  
|M200 North America|7/25/2008 12:00:00|163|1.20434529288162|1.20434529288162|  
|M200 North America|8/25/2008 12:00:00|178|1.65031343900634|1.65031343900634|  
|M200 North America|9/25/2008 12:00:00|156|1.68969399185442|1.68969399185442|  
  
> [!NOTE]  
>  Le mot clé FLATTENED a été utilisé dans cet exemple pour simplifier la présentation des résultats dans une table ; toutefois, si votre fournisseur prend en charge les ensembles de lignes hiérarchiques, vous pouvez omettre ce mot clé. Si vous omettez le mot clé FLATTENED, la requête retourne deux colonnes, la première contenant la valeur qui identifie la série de données `[Model Region]` et la deuxième contenant la table imbriquée de statistiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Exemples de requêtes de modèle de série chronologique](https://docs.microsoft.com/analysis-services/data-mining/time-series-model-query-examples)   
 [Predict &#40;DMX&#41;](../dmx/predict-dmx.md)  
  
  
