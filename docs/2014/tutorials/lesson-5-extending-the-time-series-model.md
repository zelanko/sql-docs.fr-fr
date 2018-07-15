---
title: 'Leçon 5 : Extension de la série chronologique de modèle | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7aad4946-c903-4e25-88b9-b087c20cb67d
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aab77b225eeef6844dc74deb272430b0434de71e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194389"
---
# <a name="lesson-5-extending-the-time-series-model"></a>Leçon 5 : Extension du modèle de série chronologique
  Dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise, vous pouvez ajouter de nouvelles données à un modèle de série chronologique et les incorporer automatiquement au modèle. Vous ajoutez de nouvelles données à un modèle d'exploration de données de série chronologique de l'une des deux manières suivantes :  
  
-   Utilisez une instruction PREDICTION JOIN pour joindre des données d'une source externe aux données d'apprentissage.  
  
-   Utilisez une requête singleton de prédiction pour fournir les données un secteur à la fois.  
  
 Par exemple, supposons que vous avez effectué l'apprentissage du modèle d'exploration de données sur les données de ventes existantes il y a quelques mois. Lorsque vous effectuez de nouvelles ventes, vous pouvez avoir envie de mettre à jour les prédictions de ventes afin d'incorporer ces nouvelles données. Pour cela, il vous suffit de fournir les nouveaux chiffres de ventes en tant que données d'entrée et de générer de nouvelles prédictions basées sur le jeu de données composite.  
  
## <a name="making-predictions-with-extendmodelcases"></a>Exécution de prédictions avec EXTEND_MODEL_CASES  
 Les exemples génériques suivants de prédiction de série chronologique utilisent EXTEND_MODEL_CASES. Le premier exemple vous permet de spécifier le nombre de prédictions commençant à partir de la dernière étape du modèle d'origine :  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>]  
```  
  
 Le deuxième exemple vous permet de spécifier l'étape à laquelle les prédictions doivent démarrer et celle à laquelle elles doivent se terminer. Cette option est importante lorsque vous étendez les cas de modèles parce que, par défaut, les étapes utilisées pour les requêtes de prédiction démarrent toujours à la fin de la série d'origine.  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n-start, n-end, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>}  
```  
  
 Dans ce didacticiel, vous allez créer deux types de requêtes.  
  
#### <a name="to-create-a-singleton-prediction-query-on-a-time-series-model"></a>Pour créer une requête singleton de prédiction sur un modèle de série chronologique  
  
1.  Dans **Explorateur d’objets**, avec le bouton droit de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction singleton dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
    ```  
  
     par :  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    ```  
  
     La première ligne extrait une valeur du modèle qui identifie la série.  
  
     La deuxième ligne contient la fonction de prédiction, qui reçoit 6 prédictions pour Quantity. Un alias, `PredictQty`, est affecté à la colonne des résultats de prédiction pour simplifier la compréhension des résultats.  
  
4.  Remplacez le code suivant :  
  
    ```  
    FROM <mining model>  
    ```  
  
     par :  
  
    ```  
    FROM [Forecasting_MIXED]  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    PREDICTION JOIN <source query>  
    ```  
  
     par :  
  
    ```  
    NATURAL PREDICTION JOIN   
    (  
       SELECT 1 AS [Reporting Date],  
       '10' AS [Quantity],  
       'M200 Europe' AS [Model Region]  
       UNION SELECT  
       2 AS [Reporting Date],  
       15 AS [Quantity]),  
       'M200 Europe' AS [Model Region]  
    ) AS t  
    ```  
  
6.  Remplacez le code suivant :  
  
    ```  
    [WHERE <criteria>]  
    ```  
  
     par :  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    FROM  
       [Forecasting_MIXED]  
    NATURAL PREDICTION JOIN   
       SELECT 1 AS [ReportingDate],  
      '10' AS [Quantity],  
      'M200 Europe' AS [ModelRegion]  
    UNION SELECT  
      2 AS [ReportingDate],  
      15 AS [Quantity]),  
      'M200 Europe' AS [ModelRegion]  
    ) AS t  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
7.  Sur le **fichier** menu, cliquez sur **enregistrer DMXQuery1.dmx sous**.  
  
8.  Dans le **enregistrer en tant que** boîte de dialogue, accédez au dossier approprié et nommez le fichier `Singleton_TimeSeries_Query.dmx`.  
  
9. Dans la barre d’outils, cliquez sur le **Execute** bouton.  
  
     La requête renvoie des prédictions de quantité de ventes pour le vélo M200 dans les régions Europe et Pacific.  
  
## <a name="understanding-prediction-start-with-extendmodelcases"></a>Démarrage de prédiction avec EXTEND_MODEL_CASES  
 Maintenant que vous avez créé des prédictions basées sur le modèle d'origine, et avec de nouvelles données, vous pouvez comparer les résultats pour observer comment la mise à jour des données de ventes affecte les prédictions. Avant cela, examinez le code que vous venez de créer et remarquez ce qui suit :  
  
-   Vous avez fourni de nouvelles données uniquement pour la région Europe.  
  
-   Vous avez fourni des nouvelles données uniquement pour deux mois.  
  
 Le tableau suivant montre comment les nouvelles valeurs fournies pour M200 Europe affectent les prédictions. Vous n'avez pas fourni de nouvelles données pour le produit M200 dans la région Pacific, mais cette série est présentée à titre de comparaison :  
  
 **Produit et région : M200 Europe**  
  
|||||  
|-|-|-|-|  
|||Modèle existant (`PredictTimeSeries`)|Modèle avec les données de ventes (`PredictTimeSeries` mises à jour avec `EXTEND_MODEL_CASES`)|  
|M200 Europe|25/7/2008 12:00:00 AM|77|10|  
|M200 Europe|25/8/2008 12:00:00 AM|64|15|  
|M200 Europe|25/9/2008 12:00:00 AM|59|72|  
|M200 Europe|25/10/2008 12:00:00 AM|56|69|  
|M200 Europe|25/11/2008 12:00:00 AM|56|68|  
|M200 Europe|25/12/2008 12:00:00|74|89|  
  
 **Produit et région : M200 Pacific**  
  
|||||  
|-|-|-|-|  
|||Modèle existant (`PredictTimeSeries`)|Modèle avec les données de ventes (`PredictTimeSeries` mises à jour avec `EXTEND_MODEL_CASES`)|  
|M200 Pacific|25/7/2008 12:00:00 AM|41|41|  
|M200 Pacific|25/8/2008 12:00:00 AM|44|44|  
|M200 Pacific|25/9/2008 12:00:00 AM|38|38|  
|M200 Pacific|25/10/2008 12:00:00 AM|41|41|  
|M200 Pacific|25/11/2008 12:00:00 AM|36|36|  
|M200 Pacific|25/12/2008 12:00:00|39|39|  
  
 D'après ces résultats, vous pouvez conclure deux choses :  
  
-   Les deux premières prédictions pour la série M200 Europe sont exactement les mêmes que les nouvelles données que vous avez fournies. Par sa conception, Analysis Services renvoie les nouveaux points de données réels au lieu d'élaborer une prédiction. Ceci est dû au fait que lorsque vous étendez les cas de modèles, les étapes utilisées pour les requêtes de prédiction démarrent toujours à la fin de la série d'origine. Par conséquent, si vous ajoutez deux nouveaux points de données, les deux premières prédictions renvoyées et les nouvelles données se chevauchent.  
  
-   Après avoir utilisé tous les nouveaux points de données, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] élabore des prédictions selon le modèle mis à jour. Par conséquent, à compter de septembre 2005, vous pouvez observer la différence entre les prédictions pour M200 Europe depuis le modèle d'origine, dans la colonne gauche, et le modèle qui utilise EXTEND_MODEL_CASES, dans la colonne droite. Les prédictions sont différentes parce que le modèle a été mis à jour avec les nouvelles données.  
  
## <a name="using-start-and-end-time-steps-to-control-predictions"></a>Utilisation d'étapes de début et de fin pour contrôler des prédictions  
 Lorsque vous étendez un modèle, les nouvelles données sont toujours jointes à la fin de la série. Toutefois, à des fins de prédiction, les tranches de temps utilisées pour les requêtes de prédiction commencent toujours à la fin de la série d'origine. Si vous souhaitez obtenir uniquement les nouvelles prédictions lorsque vous ajoutez les nouvelles données, vous devez spécifier le point de départ sous la forme d'un nombre de tranches de temps. Par exemple, si vous ajoutez deux nouveaux points de données et souhaitez élaborer quatre nouvelles prédictions, vous devez procéder comme suit :  
  
-   Créez une jointure PREDICTION JOIN sur un modèle de série chronologique et spécifiez deux mois de nouvelles données.  
  
-   Demandez des prédictions pour quatre tranches de temps, dont le point de départ est la tranche de temps 3 et le point de terminaison la tranche de temps 6.  
  
 En d’autres termes, si vos nouvelles données contiennent n tranches horaires et que vous demandez des prédictions pour les étapes 1 à n, les prédictions coïncideront avec la même période que les nouvelles données. Pour obtenir de nouvelles prédictions pour des périodes non couvertes par vos données, vous devez commencer les prédictions à la tranche de temps n+1 après la nouvelle série de données ou vous assurer de demander des tranches de temps supplémentaires.  
  
> [!NOTE]  
>  Vous ne pouvez pas effectuer de prédictions historiques lorsque vous ajoutez de nouvelles données.  
  
 L'exemple suivant présente l'instruction DMX qui vous permet d'obtenir uniquement les nouvelles prédictions pour les deux séries mentionnées dans l'exemple précédent.  
  
```  
SELECT [Model Region],  
PredictTimeSeries([Quantity],3,6, EXTEND_MODEL_CASES) AS PredictQty  
FROM  
   [Forecasting_MIXED]  
NATURAL PREDICTION JOIN   
   SELECT 1 AS [ReportingDate],  
  '10' AS [Quantity],  
  'M200 Europe' AS [ModelRegion]  
UNION SELECT  
  2 AS [ReportingDate],  
  15 AS [Quantity]),  
  'M200 Europe' AS [ModelRegion]  
) AS t  
WHERE [ModelRegion] = 'M200 Europe'  
```  
  
 Les résultats de prédiction démarrent à la tranche de temps 3, qui se situe après les 2 mois de nouvelles données que vous avez fournis.  
  
 **Produit et région : M200 Europe**  
  
 Modèle avec les données mises à jour (PredictTimeSeries avec EXTEND_MODEL_CASES)  
  
||||  
|-|-|-|  
|M200 Europe|25/9/2008 12:00:00 AM|72|  
|M200 Europe|25/10/2008 12:00:00 AM|69|  
|M200 Europe|25/11/2008 12:00:00 AM|68|  
|M200 Europe|25/12/2008 12:00:00|89|  
  
## <a name="making-predictions-with-replacemodelcases"></a>Exécution de prédictions avec REPLACE_MODEL_CASES  
 Le remplacement des cas de modèles s'avère utile lorsque vous souhaitez effectuer l'apprentissage d'un modèle sur un ensemble de cas, puis appliquer ce modèle à une série de données différente. Une description détaillée de ce scénario est présentée dans [leçon 2 : génération d’un scénario de prévision &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes de modèle de série chronologique](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)  
  
  
