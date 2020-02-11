---
title: 'Leçon 4 : création de prédictions de série chronologique à l’aide de DMX | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6b883e43-209d-489a-8dc3-9349f88acae8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 772e5f5f71ca82dd18fec48730522c80e907414f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63312092"
---
# <a name="lesson-4-creating-time-series-predictions-using-dmx"></a>Leçon 4 : Création de prédictions de série chronologique à l'aide d'extensions DMX
  Dans cette leçon et dans la leçon suivante, vous allez utiliser les extensions DMX (Data Mining Extensions) pour créer différents types de prédictions en fonction des modèles de série chronologique que vous avez créés au cours de la [leçon 1 : création d’un modèle](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md) d’exploration de données de série chronologique et d’une structure d’exploration de données, ainsi que [leçon 2 : ajout de modèles d’exploration de](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)données  
  
 Avec un modèle de série chronologique, de nombreuses options sont à votre disposition pour élaborer des prédictions :  
  
-   Utilisation des modèles et données existants dans le modèle d'exploration de données  
  
-   Utilisation des modèles existants dans le modèle d'exploration de données mais fourniture de nouvelles données  
  
-   Ajout de nouvelles données au modèle ou mise à jour du modèle  
  
 La syntaxe permettant d'effectuer ces types de prédictions est résumée ci-dessous :  
  
 Prédiction de série chronologique par défaut  
 Utilisez [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) pour retourner le nombre spécifié de prédictions à partir du modèle d’exploration de données formé.  
  
 Par exemple, consultez [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) ou [exemples de requêtes de modèle de série chronologique](../../2014/analysis-services/data-mining/time-series-model-query-examples.md).  
  
 EXTEND_MODEL_CASES  
 Utilisez [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) avec l’argument EXTEND_MODEL_CASES pour ajouter de nouvelles données, étendre la série et créer des prédictions basées sur le modèle d’exploration de données mis à jour.  
  
 Ce didacticiel contient un exemple de la manière d'utiliser EXTEND_MODEL_CASES.  
  
 REPLACE_MODEL_CASES  
 Utilisez [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) avec l’argument REPLACE_MODEL_CASES pour remplacer les données d’origine par une nouvelle série de données, puis créez des prédictions en fonction de l’application des modèles dans le modèle d’exploration de données à la nouvelle série de données.  
  
 Pour obtenir un exemple d’utilisation de REPLACE_MODEL_CASES, consultez [leçon 2 : génération d’un scénario de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
-   créer une requête pour obtenir les prédictions par défaut basées sur des données existantes.  
  
 Au cours de la leçon suivante, vous allez effectuer les tâches connexes suivantes :  
  
-   créer une requête pour fournir de nouvelles données et obtenir des prédictions mises à jour.  
  
 En plus de pouvoir créer manuellement des requêtes en utilisant des extensions DMX, vous pouvez également créer des prédictions à l'aide du Générateur de requêtes de prédiction dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="simple-time-series-prediction-query"></a>Requête de prédiction de série chronologique simple  
 La première étape consiste à utiliser l'instruction `SELECT FROM` avec la fonction `PredictTimeSeries` pour créer des prédictions de série chronologique. Les modèles de série chronologique prennent en charge une syntaxe simplifiée pour créer des prédictions : vous n'avez pas besoin de fournir d'entrées, mais vous devez uniquement spécifier le nombre de prédictions à créer. L'exemple générique suivant présente l'instruction que vous utiliserez :  
  
```  
SELECT <select list>   
FROM [<mining model name>]   
WHERE [<criteria>]  
```  
  
 La liste de sélection peut contenir des colonnes du modèle, telles que le nom de la gamme de produits pour laquelle vous créez les prédictions ou des fonctions de prédiction, telles que le [décalage &#40;dmx&#41;](/sql/dmx/lag-dmx) ou [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx), qui sont spécifiquement pour les modèles d’exploration de données de série chronologique.  
  
#### <a name="to-create-a-simple-time-series-prediction-query"></a>Pour créer une requête de prédiction de série chronologique simple  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]droit sur l’instance de, pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <select list>   
    ```  
  
     par :  
  
    ```  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    ```  
  
     La première ligne extrait une valeur du modèle d'exploration de données qui identifie la série.  
  
     Les deuxième et troisième lignes utilisent la fonction `PredictTimeSeries`. Chaque ligne prédit un attribut différent, `[Quantity]` ou `[Amount]`. Les nombres indiqués après les noms des attributs prédictibles précisent le nombre d'étapes à prédire.  
  
     La clause `AS` est utilisée pour fournir un nom à la colonne renvoyée par chaque fonction de prédiction. Si vous ne fournissez pas d'alias, les deux colonnes sont renvoyées avec l'étiquette `Expression` par défaut.  
  
4.  Remplacez le code suivant :  
  
    ```  
    [<mining model>]   
    ```  
  
     par :  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    WHERE [criteria>]   
    ```  
  
     par :  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    SELECT  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    FROM   
    [Forecasting_MIXED]  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
6.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
7.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `SimpleTimeSeriesPrediction.dmx`.  
  
8.  Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
     La requête renvoie 6 prédictions pour chacune des deux combinaisons de produit et région spécifiées dans la clause `WHERE`.  
  
 Dans la leçon suivante, vous allez créer une requête qui fournit de nouvelles données au modèle, puis comparer les résultats de cette prédiction avec celle que vous venez de créer.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Leçon 5 : Extension du modèle de série chronologique](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
  
## <a name="see-also"></a>Voir aussi  
 [PredictTimeSeries&#41;DMX &#40;](/sql/dmx/predicttimeseries-dmx)   
 [Retard &#40;&#41;DMX](/sql/dmx/lag-dmx)   
 [Exemples de requêtes de modèle de série chronologique](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Leçon 2 : génération d’un scénario de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
  
