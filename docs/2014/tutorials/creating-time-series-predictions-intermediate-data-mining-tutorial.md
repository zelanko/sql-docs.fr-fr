---
title: Création de prédictions de série chronologique (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: fb22cffa-ac99-4d34-ac4a-9c93068e33e8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 109c4eb07dd34aa5ef3e41d794edfc39ffffcac8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119869"
---
# <a name="creating-time-series-predictions-intermediate-data-mining-tutorial"></a>Création de prédictions de série chronologique (Didacticiel intermédiaire sur l'exploration de données)
  Dans les tâches précédentes de cette leçon, vous avez créé un modèle de série chronologique et exploré les résultats. Par défaut, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] crée toujours un jeu de cinq (5) prédictions pour un modèle de série chronologique et affiche les valeurs prédites dans le graphique de prévision. Toutefois, vous pouvez également créer des prévisions en générant des requêtes de prédiction DMX (Data Mining Extensions).  
  
 Dans cette tâche, vous allez créer une requête de prédiction qui génère les mêmes prédictions que celles affichées dans la visionneuse. Cette tâche suppose que vous avez déjà suivi les leçons du didacticiel sur l'exploration de données de base et que vous savez utiliser le Générateur de requêtes de prédiction. Vous allez maintenant apprendre à créer des requêtes spécifiques aux modèles de série chronologique.  
  
## <a name="creating-time-series-predictions"></a>Création de prédictions de séries chronologiques  
 La première étape dans la création d'une requête de prédiction consiste généralement à sélectionner un modèle d'exploration de données et une table d'entrée. Toutefois, un modèle de série chronologique ne nécessite pas d'entrée supplémentaire pour une prédiction normale. Par conséquent, vous n'avez pas besoin de spécifier une nouvelle source de données pour faire des prédictions, sauf si vous ajoutez des données au modèle ou en remplacez.  
  
 Pour cette leçon, vous devez spécifier le nombre d'étapes de prédiction. Vous pouvez spécifier le nom de la série pour obtenir une prédiction d'une combinaison particulière d'un produit et d'une région.  
  
#### <a name="to-select-a-model-and-input-table"></a>Pour sélectionner un modèle et une table d'entrée  
  
1.  Sur le **prévision de modèle d’exploration de données** onglet du Concepteur d’exploration de données, dans le **Mining Model** , cliquez sur **sélectionner un modèle**.  
  
2.  Dans le **sélectionner un modèle d’exploration de données** boîte de dialogue, développez la structure Forecasting, sélectionnez le **Forecasting** de modèle dans la liste, puis cliquez sur **OK**.  
  
3.  Ignorer le **sélectionner une ou plusieurs tables d’entrée** boîte.  
  
    > [!NOTE]  
    >  Pour un modèle de série chronologique, vous n'avez pas besoin de spécifier une entrée séparée sauf si vous faites de la prédiction croisée.  
  
4.  Dans le **Source** colonne, dans la grille sur la **prévision de modèle d’exploration de données** onglet, cliquez sur la cellule dans la première ligne vide, puis sélectionnez **modèle d’exploration de données de prévision**.  
  
5.  Dans le **champ** colonne, sélectionnez **Model Region**.  
  
     Cette action ajoute l'identificateur de série à la requête de prédiction pour indiquer la combinaison de modèle et de région à laquelle la prédiction s'applique.  
  
6.  Cliquez sur la ligne vide suivante dans le **Source** colonne, puis sélectionnez **fonction de prédiction**.  
  
7.  Dans le **champ** colonne, sélectionnez **PredictTimeSeries**.  
  
    > [!NOTE]  
    >  Vous pouvez utiliser également la fonction `Predict` avec des modèles de série chronologique. Toutefois, par défaut, la fonction Predict crée une seule prédiction pour chaque série. Par conséquent, pour spécifier plusieurs étapes de prédiction, vous devez utiliser le **PredictTimeSeries** (fonction).  
  
8.  Dans le **modèle d’exploration de** volet, sélectionnez la colonne du modèle d’exploration de données, **quantité.** Faites glisser Amount vers la **critères/argument** zone pour le **PredictTimeSeries** fonction que vous avez ajouté précédemment.  
  
9. Cliquez sur le **critères/argument** , puis tapez une virgule, suivie **5**, après le nom du champ.  
  
     Le texte dans le **critères/argument** boîte doit désormais afficher les éléments suivants :  
  
     `[Forecasting].[Amount],5`  
  
10. Dans le **Alias** colonne, tapez `PredictAmount`.  
  
11. Cliquez sur la ligne vide suivante dans le **Source** colonne, puis sélectionnez **fonction de prédiction** à nouveau.  
  
12. Dans le **champ** colonne, sélectionnez **PredictTimeSeries**.  
  
13. Dans le **Mining Model** volet, sélectionnez la colonne Quantity, puis faites-le glisser vers le **critères/argument** zone pour la deuxième **PredictTimeSeries** (fonction).  
  
14. Cliquez sur le **critères/argument** , puis tapez une virgule, suivie **5**, après le nom du champ.  
  
     Le texte dans le **critères/argument** boîte doit désormais afficher les éléments suivants :  
  
     `[Forecasting].[ Quantity],5`  
  
15. Dans le **Alias** colonne, tapez `PredictQuantity`.  
  
16. Cliquez sur **basculer vers l’affichage des résultats de requête**.  
  
     Les résultats de la requête sont affichés sous forme de tableau.  
  
 N'oubliez pas que vous avez créé trois types différents de résultats dans le générateur de requête, un type qui utilise des valeurs d'une colonne, et deux autres types qui reçoivent des valeurs prédites d'une fonction de prédiction. Par conséquent, les résultats de la requête contiennent trois colonnes séparées. La première colonne contient la liste des combinaisons de produit et de région. Les deuxième et troisième colonnes contiennent chacune une table imbriquée de résultats de prédiction. Chaque table imbriquée contient les valeurs prédites et d'étape, comme dans le tableau suivant :  
  
 Exemples de résultats (les montants sont tronqués à deux décimales) :  
  
 **M200 Europe PredictAmount**  
  
|$TIME|Montant|  
|-----------|------------|  
|25/7/2008|99978.00|  
|25/8/2008|145575.07|  
|25/9/2008|116835.19|  
|25/10/2008|116537.38|  
|25/11/2008|107760.55|  
  
 **M200 Europe PredictQuantity**  
  
|$TIME|Quantité|  
|-----------|--------------|  
|25/7/2008|52|  
|25/8/2008|67|  
|25/9/2008|58|  
|25/10/2008|57|  
|25/11/2008|54|  
  
 **M200 North America - PredictAmount**  
  
|$TIME|Montant|  
|-----------|------------|  
|25/7/2008|348533.93|  
|25/8/2008|340097.98|  
|25/9/2008|257986.19|  
|25/10/2008|374658.24|  
|25/11/2008|379241.44|  
  
 **M200 North America - PredictQuantity**  
  
|$TIME|Quantité|  
|-----------|--------------|  
|25/7/2008|272|  
|25/8/2008|152|  
|25/9/2008|250|  
|25/10/2008|181|  
|25/11/2008|290|  
  
> [!WARNING]  
>  Les dates utilisées dans l'exemple de base de données ont changé pour cette version. Si vous utilisez une version antérieure des exemples de données, vous pouvez obtenir des résultats différents.  
  
## <a name="saving-the-prediction-results"></a>Enregistrement des résultats de prédiction  
 Différentes options s'offrent à vous pour l'utilisation des résultats de prédiction. Vous pouvez aplatir les résultats, copier les données de la vue Résultats et les coller dans une feuille de calcul Excel ou un autre fichier.  
  
 Pour simplifier le processus d'enregistrement des résultats, le Concepteur d'exploration de données fournit également la possibilité d'enregistrer les données dans une vue de source de données. La fonctionnalité d'enregistrement des résultats dans une vue de source de données est disponible uniquement dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Les résultats peuvent être stockées uniquement dans un format à plat.  
  
#### <a name="to-flatten-the-results-in-the-results-pane"></a>Pour aplatir les résultats dans le volet Résultats  
  
1.  Dans le Générateur de requêtes de prédiction, cliquez sur **basculer vers l’affichage de conception de requête**.  
  
     La vue se modifie pour autoriser l'édition manuelle du texte de la requête DMX.  
  
2.  Tapez le mot clé `FLATTENED` après le mot clé `SELECT`. Le texte de la requête tout entière doit se présenter comme suit :  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    ```  
  
3.  Éventuellement, vous pouvez taper une clause pour restreindre les résultats, comme l'exemple suivant :  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    WHERE [Forecasting].[Model Region] = 'M200 North America'   
    OR [Forecasting].[Model Region] = 'M200 Europe'  
  
    ```  
  
4.  Cliquez sur **basculer vers l’affichage des résultats de requête**.  
  
#### <a name="to-export-prediction-query-results"></a>Pour exporter des résultats d'une requête de prédiction  
  
1.  Cliquez sur **enregistrer les résultats de la requête**.  
  
2.  Dans le **enregistrer le résultat de requête Data Mining** boîte de dialogue pour **Source de données**, sélectionnez [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]. Vous pouvez également créer une source de données si vous souhaitez enregistrer les données dans une base de données relationnelles différente.  
  
3.  Dans le **nom de la Table** colonne, type de nom, de la table temporaire nouveau comme **tester les prédictions**.  
  
4.  Cliquez sur **Enregistrer**.  
  
    > [!NOTE]  
    >  Pour consulter la table que vous avez créée, créez une connexion au moteur de base de données de l'instance où vous avez enregistré les données, et créez une requête.  
  
## <a name="conclusion"></a>Conclusion  
 Vous avez appris à générer un modèle de série chronologique de base, interpréter les prédictions et créer des prédictions.  
  
 Les tâches restantes dans ce didacticiel sont facultatives et décrivent les prédictions avancées de série chronologique. Si vous décidez de continuer, vous allez apprendre à ajouter de nouvelles données à votre modèle et à créer des prédictions sur la série étendue. Vous apprendrez également comment effectuer la prédiction croisée en utilisant la tendance du modèle mais en remplaçant les données à une nouvelle série de données.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Avancée des prédictions de série chronologique &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes de modèle de séries chronologiques](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
