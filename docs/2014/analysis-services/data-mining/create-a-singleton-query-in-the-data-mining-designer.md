---
title: Créer une requête Singleton dans le Concepteur d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- singleton queries [Analysis Services]
- Mining Model Prediction [Analysis Services], singleton queries
ms.assetid: 6cdca8a0-cf16-46eb-a652-0bff820625ab
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 795347e0ef2bdee226daff57e85e2b02f8b00c9e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66085306"
---
# <a name="create-a-singleton-query-in-the-data-mining-designer"></a>créer une requête singleton dans le Concepteur d'exploration de données
  Une requête singleton est utile si vous voulez créer une prédiction pour un seul cas. Pour plus d’informations sur les requêtes singleton, consultez [Requêtes d’exploration de données](data-mining-queries.md).  
  
 Sous l’onglet **Prévision de modèle d’exploration de données** du Concepteur d’exploration de données, vous pouvez créer différents types de requêtes. Vous pouvez créer une requête en utilisant le concepteur ou en tapant des instructions DMX (Data Mining Extensions). Vous pouvez également utiliser le concepteur pour commencer, puis modifier la requête créée en modifiant les instructions DMX ou en ajoutant une clause WHERE ou ORDER BY.  
  
 Pour basculer entre l'affichage de conception de requête et l'affichage du texte de la requête, cliquez sur le premier bouton dans la barre d'outils. Lorsque vous vous trouvez dans la vue de texte de requête, vous pouvez afficher le code créé par le Générateur de requêtes de prédiction. Vous pouvez également exécuter la requête, la modifier et exécuter la requête modifiée. Toutefois, la requête modifiée n'est pas conservée si vous réaffichez la vue de conception de requête.  
  
 Le code suivant montre un exemple de requête singleton sur le modèle de publipostage ciblé TM_Decision_Tree.  
  
```  
SELECT [Bike Buyer], PredictProbability([Bike Buyer]) as ProbableBuyer  
FROM [TM_Decision_Tree]  
NATURAL PREDICTION JOIN  
(SELECT '2' AS [Number Children At Home], '45' as [Age])  
AS [t]  
```  
  
 Les étapes suivantes expliquent comment créer cette requête de prédiction.  
  
### <a name="to-create-a-singleton-query-by-using-the-data-mining-designer"></a>Pour créer une requête singleton à l'aide du Concepteur d'exploration de données  
  
1.  Cliquez sur **Prévision de modèle d’exploration de données** dans le Concepteur d’exploration de données.  
  
2.  Cliquez sur **Sélectionner un modèle** dans la table **Modèle d’exploration de données** .  
  
     La boîte de dialogue **Sélectionner un modèle d’exploration de données** s’ouvre pour afficher toutes les structures d’exploration de données qui existent dans le projet actuel.  
  
     Sélectionnez le modèle à utiliser pour créer une prédiction.  
  
     Par exemple, pour créer l’exemple de code donné au début de cette rubrique, sélectionnez TM_Decision_Tree, puis cliquez sur **OK**.  
  
3.  Cliquez sur **Requête singleton** dans la barre d’outils de l’onglet **Prévision de modèle d’exploration de données** .  
  
     La table **Entrée de requête singleton** s’affiche dans l’onglet avec les colonnes mappées automatiquement aux colonnes de la table **Modèle d’exploration de données** .  
  
4.  Dans la table **Entrée de requête singleton** , sélectionnez les valeurs dans la colonne **Valeur** pour décrire le cas pour lequel vous voulez créer une prévision.  
  
     Par exemple, sélectionnez **2** pour **Number Children At Home**, puis tapez `45` pour **âge**.  
  
5.  Faites glisser une colonne prédictible de la table **Modèle d’exploration** vers la colonne **Source** au bas de l’onglet. Vous pouvez éventuellement taper un alias pour la colonne.  
  
     Par exemple, faites glisser **Bike Buyer** vers la colonne **Source** .  
  
6.  Ajoutez des fonctions supplémentaires à la requête en sélectionnant **Fonction de prédiction** ou **Expression personnalisée** dans la liste déroulante de la colonne **Source** .  
  
     Par exemple, cliquez sur **Fonction de prédiction**et sélectionnez **PredictProbability**.  
  
7.  Cliquez sur **Critères/Argument** dans la ligne **PredictProbability** , puis tapez le nom de la colonne à prédire et éventuellement une valeur spécifique à prédire.  
  
     Par exemple, tapez `[Bike Buyer], 1`.  
  
8.  Cliquez sur la zone **Alias** dans la ligne **PredictProbability** , puis tapez un nom pour faire référence à la nouvelle colonne.  
  
     Par exemple, tapez `ProbableBuyer`.  
  
9. Cliquez sur **Basculer vers l’affichage du résultat de la requête** dans la barre d’outils de l’onglet **Prévision de modèle d’exploration de données** .  
  
     Un nouvel écran s'affiche avec le résultat de la requête. Pour examiner l’instruction DMX que vous venez de créer, cliquez sur **SQL**.  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes de prédiction &#40;Exploration de données&#41;](prediction-queries-data-mining.md)  
  
  
