---
title: À l’aide de données de remplacement (didacticiel d’exploration de données intermédiaire) des prédictions de série chronologique | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a23a6e1d-1d49-41ea-8314-925dc8e4df5e
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c96b70775105ea9446810ac3b064ae7cb07d4337
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63312878"
---
# <a name="time-series-predictions-using-replacement-data-intermediate-data-mining-tutorial"></a>Prédictions de série chronologique à l'aide des données de remplacement (Didacticiel intermédiaire sur l'exploration de données)
  Dans cette tâche, vous allez générer un nouveau modèle basé sur des données de ventes internationales. Ensuite, vous apprendrez à créer une requête de prédiction qui applique le modèle de ventes internationales à chacune des régions.  
  
## <a name="building-a-general-model"></a>Génération d'un modèle général  
 N'oubliez pas que votre analyse des résultats du modèle d'exploration de données d'origine a révélé des différences majeures entre les régions et entre certaines gammes de produits. Par exemple, les ventes en Amérique du Nord étaient élevées pour le modèle M200, tandis que les ventes du modèle T1000 étaient inférieures. Toutefois, l’analyse est compliquée par le fait que certaines séries ne contenaient pas de volume de données, ou données commençaient à un autre point dans le temps. Certaines données sont également manquantes.  
  
 ![Série de prédire la quantité M200 et T1000](../../2014/tutorials/media/6series-defaultforecasting.gif "M200 et T1000 la quantité de prédiction de série")  
  
 Pour résoudre certains de ces problèmes de qualité des données, vous décidez de fusionner les données des ventes dans le monde entier, puis vous utilisez cet ensemble des tendances de ventes générales pour générer un modèle qui peut être appliqué pour prédire les ventes futures dans n'importe quelle région.  
  
 Lorsque vous créez des prédictions, vous utiliserez le modèle généré par la formation sur les données de ventes internationales, mais vous remplacerez les points de données historiques par les données de ventes pour chaque région. Ainsi, la forme de la tendance est conservée mais les valeurs prédites sont alignées sur les chiffres de vente historiques de chaque région et modèle.  
  
## <a name="performing-cross-prediction-with-a-time-series-model"></a>Exécution de la prédiction croisée à l'aide d'un modèle de série chronologique  
 L'utilisation des données d'une série pour prédire des tendances dans une autre série est un processus appelé prédiction croisée. Vous pouvez utiliser la prédiction croisée dans de nombreux scénarios : par exemple, vous pouvez décider que les ventes de télévision sont un bon indicateur de prédiction d'activité économique globale, puis appliquer un modèle qualifié sur les ventes de télévision aux données économiques générales.  
  
 SQL Server Data Mining, vous effectuez la prédiction croisée à l’aide du paramètre REPLACE_MODEL_CASES au sein des arguments à la fonction, [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx).  
  
 Dans la tâche suivante, vous allez apprendre à utiliser REPLACE_MODEL_CASES. Vous allez utiliser les données de ventes internationales fusionnées pour générer un modèle, puis créer une requête de prédiction qui mappe le modèle général aux données de remplacement.  
  
 Cette rubrique suppose que vous savez aujourd'hui comment générer des modèles d'exploration de données et ainsi les instructions permettant de générer le modèle ont été simplifiées.  
  
#### <a name="to-build-a-mining-structure-and-mining-model-using-the-aggregated-data"></a>Pour générer une structure d'exploration de données et un modèle d'exploration de données à l'aide des données agrégées  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **des Structures d’exploration de données**, puis sélectionnez **nouvelle Structure d’exploration de données** pour démarrer l’Assistant exploration de données.  
  
2.  Dans l'Assistant Exploration de données, effectuez les sélections suivantes :  
  
    -   Algorithme : Microsoft Time Series  
  
    -   Utilisez la source de données que vous avez générée précédemment dans cette leçon avancée comme source pour le modèle. Consultez [avancé des prédictions de série chronologique &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md).  
  
         Vue de source de données : `AllRegions`  
  
    -   Choisissez les colonnes suivantes pour la clé de série et la clé de temps :  
  
         Temps clé : ReportingDate  
  
         Clé : Région  
  
    -   Choisissez les colonnes suivantes pour `Input` et `Predict` :  
  
         SumQty  
  
         SumAmt  
  
         AvgAmt  
  
         AvgQty  
  
    -   Pour **nom de la structure d’exploration de données**, type : `All Regions`  
  
    -   Pour **nom du modèle d’exploration de données**, type : `All Regions`  
  
3.  Traitez la nouvelle structure et le nouveau modèle.  
  
#### <a name="to-build-the-prediction-query-and-map-the-replacement-data"></a>Pour générer la requête de prédiction et mappez les données de remplacement  
  
1.  Si le modèle n’est pas déjà ouvert, double-cliquez sur la structure AllRegions et dans le Concepteur d’exploration de données, cliquez sur le **prévision de modèle d’exploration de données** onglet.  
  
2.  Dans le **Mining Model** volet, le modèle AllRegions doit déjà être sélectionné. Si elle n’est pas sélectionnée, cliquez sur **sélectionner un modèle**, puis sélectionnez le modèle, AllRegions.  
  
3.  Dans le **sélectionner une ou plusieurs tables d’entrée** volet, cliquez sur **sélectionner la Table de cas**.  
  
4.  Dans le **sélectionner une Table** boîte de dialogue, modifier les données source par T1000 Pacific Region, puis cliquez sur **OK**.  
  
5.  Cliquez sur la ligne de jointure entre le modèle d’exploration de données et les données d’entrée et sélectionnez **modifier les connexions**. Mappez les données dans la vue de source de données du modèle comme suit :  
  
    1.  Vérifiez que la colonne ReportingDate dans le modèle d’exploration de données est mappée à la colonne ReportingDate dans les données d’entrée.  
  
    2.  Dans le **modifier le mappage** boîte de dialogue, dans la ligne de la colonne du modèle AvgQty, cliquez sur sous **colonne de Table** , puis sélectionnez T1000 Pacific.Quantity. Cliquez sur **OK**.  
  
         Cette étape mappe la colonne que vous avez créée dans le modèle pour la quantité moyenne de prédiction aux données réelles de la série T1000 pour la quantité de ventes.  
  
    3.  Ne mappez pas la colonne région dans le modèle à n’importe quelle colonne d’entrée.  
  
         Étant donné que le modèle agrégeait les données de toutes les séries, il n'existe aucune correspondance des valeurs des séries telles que T1000 Pacific, et une erreur est générée lorsque la requête de prédiction s'exécute.  
  
6.  Vous allez maintenant générer la requête de prédiction.  
  
     Ajoutez d'abord une colonne aux résultats qui produit comme sorties l'étiquette AllRegions du modèle ayant les prédictions. De cette manière, vous savez que les résultats ont été basés sur le modèle général.  
  
    1.  Dans la grille, cliquez sur la première ligne vide, sous **Source**, puis sélectionnez le modèle d’exploration de données de AllRegions.  
  
    2.  Pour **champ**, sélectionnez la région.  
  
    3.  Pour **Alias**, type **modèle utilisé**.  
  
7.  Ajoutez ensuite une autre étiquette aux résultats, afin de pouvoir identifier la série concernée par les prédictions.  
  
    1.  Cliquez sur une ligne vide, puis, sous **Source**, sélectionnez **Expression personnalisée**.  
  
    2.  Dans le **Alias** colonne, tapez **ModelRegion**.  
  
    3.  Dans le **critères/Argument** colonne, tapez `'T1000 Pacific'`.  
  
8.  Vous allez maintenant définir la fonction de prédiction croisée.  
  
    1.  Cliquez sur une ligne vide, puis, sous **Source**, sélectionnez **fonction de prédiction**.  
  
    2.  Dans le **champ** colonne, sélectionnez **PredictTimeSeries**.  
  
    3.  Pour **Alias**, type **valeurs prédites**.  
  
    4.  Faites glisser le champ AvgQty à partir de la **Mining Model** volet dans le **critères/Argument** colonne à l’aide de l’opération de glisser -déplacer.  
  
    5.  Dans le **critères/Argument** colonne, après le nom de champ, tapez le texte suivant : `,5, REPLACE_MODEL_CASES`  
  
         Le texte complet de le **critères/Argument** zone de texte doit être comme suit : `[AllRegions].[AvgQty],5,REPLACE_MODEL_CASES`  
  
9. Cliquez sur **résultats**.  
  
## <a name="creating-the-cross-prediction-query-in-dmx"></a>Création de la requête de prédiction croisée dans DMX  
 Vous avez peut-être remarqué un problème avec la prédiction croisée : à savoir que pour appliquer le modèle général à une autre série de données, telle que le modèle de produit T1000 dans la région North America, vous devez créer une autre requête pour chaque série afin de pouvoir mapper chaque ensemble d'entrées au modèle.  
  
 Toutefois, plutôt que de générer la requête dans le concepteur, vous pouvez basculer sur la vue DMX et modifier l'instruction DMX que vous avez créée. Par exemple, l'instruction DMX suivante représente la requête que vous venez de créer :  
  
```  
SELECT  
      ([All Regions].[Region]) as [Model Used],  
      ('T-1000 Pacific') as [ModelRegion],  
      (PredictTimeSeries([All Regions].[Avg Qty],5, REPLACE_MODEL_CASES)) as [Predicted Quantity]  
     FROM [All Regions]  
PREDICTION JOIN  
    OPENQUERY([Adventure Works DW2003R2], 'SELECT [ReportingDate] FROM  
      (  
       SELECT  ReportingDate, ModelRegion, Quantity, Amount   
       FROM dbo.vTimeSeries   
       WHERE (ModelRegion = N''T1000 Pacific'')  
       ) as [T1000 Pacific]    ')   
    AS t  
ON   
[All Regions].[Reporting Date] = t.[ReportingDate]   
AND   
[All Regions].[Avg Qty] = t.[Quantity]  
```  
  
 Pour appliquer ceci à un autre modèle, modifiez simplement l'instruction de requête pour remplacer la condition de filtre et pour mettre à jour les étiquettes associées à chaque résultat.  
  
 Par exemple, si vous modifiez les conditions de filtre et les intitulés de colonne en remplaçant « Pacific » par « North America », vous recevrez des prédictions pour le produit T1000 en Amérique du Nord, selon le modèle général.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Comparaison de prédictions pour les modèles de prévision &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes de modèle de série chronologique](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)  
  
  
