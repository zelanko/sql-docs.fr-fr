---
title: Validation croisée (compléments d’exploration de données SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cross-validation
- partitioning data [data mining]
- mining models, testing
ms.assetid: bf9483b3-4099-41c4-bbc5-da7005e07bcd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0cc3a132792cca8ecdf5a33a2fe4e4d40116c497
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086651"
---
# <a name="cross-validation-sql-server-data-mining-add-ins"></a>Validation croisée (Compléments d'exploration de données SQL Server)
  ![Bouton Validation croisée, ruban Exploration de données](media/dmc-xvalid.gif "Bouton Validation croisée, ruban Exploration de données")  
  
 La validation croisée est un outil standard dans le domaine de l'analyse et une fonction importante dans le développement et l'optimisation de modèles d'exploration de données. Vous recourez à la validation croisée après avoir créé un modèle d'exploration de données afin d'établir la validité du modèle et de comparer ses résultats à d'autres modèles d'exploration de données connexes.  
  
 La validation croisée comprend deux phases, l'apprentissage et la génération des rapports. Vous allez accomplir les étapes ci-dessous :  
  
-   sélectionner un modèle ou une structure d'exploration de données cible ;  
  
-   spécifier la valeur cible, le cas échéant ;  
  
-   Spécifiez le nombre de sections croisées, ou *pliures*, dans lesquelles partitionner les données de la structure.  
  
 L’Assistant **validation croisée** crée ensuite un nouveau modèle sur chacun des plis, teste le modèle sur les autres plis, puis signale la précision du modèle. Une fois l’exécution terminée, l’Assistant **validation croisée** crée un rapport qui vous indique les mesures pour chaque pli et fournit un résumé du modèle dans l’agrégat. Ces informations peuvent être utilisées pour déterminer la qualité des données sous-jacentes pour un modèle, ou pour comparer des modèles différents reposant sur les mêmes données.  
  
## <a name="using-the-cross-validation-wizard"></a>Utilisation de l'Assistant Validation croisée  
 Vous pouvez utiliser la validation croisée à la fois sur les modèles temporaires et les modèles stockés sur une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
#### <a name="to-create-a-cross-validation-report"></a>Pour créer un rapport de validation croisée  
  
1.  Dans le groupe **précision et validation** du ruban **exploration de données** , cliquez sur **validation croisée**.  
  
2.  Dans la boîte de dialogue **Sélectionner une structure ou un modèle** , sélectionnez une structure d’exploration de données ou un modèle d’exploration de données existant. Si vous sélectionnez une structure, l'Assistant utilisera la validation croisée sur tous les modèles basés sur cette structure et ayant le même attribut prévisible spécifié. Si vous sélectionnez un modèle, l'Assistant utilisera la validation croisée uniquement sur ce modèle.  
  
3.  Dans la boîte de dialogue **spécifier les paramètres de validation croisée** , dans la zone **nombre de replis** , choisissez le nombre de replis entre lesquels diviser le jeu de données. Un repli est une section des données croisée sélectionnée aléatoirement.  
  
4.  Si vous le souhaitez, définissez le nombre maximal de lignes à utiliser dans la validation croisée en tapant un nombre dans la zone de texte nombre **maximal de lignes** .  
  
    > [!NOTE]  
    >  Plus vous utilisez de lignes, plus les résultats seront exacts. Toutefois, le temps de traitement peut également s'allonger considérablement. Le nombre que vous choisissez dépend de vos données, mais en général, vous devez choisir le nombre le plus élevé sans compromettre la performance. Pour améliorer la performance, vous pouvez également spécifier moins de replis.  
  
5.  Sélectionnez une colonne dans la liste déroulante **attribut cible** . La liste affiche uniquement les colonnes configurées en tant qu'attributs prévisibles lorsque vous avez créé le modèle à l'origine. Le modèle peut contenir plusieurs attributs prévisibles, mais vous ne pouvez en choisir qu'un seul.  
  
6.  Sélectionnez une valeur dans la liste déroulante **État cible** .  
  
     Si la colonne prévisible contient des données numériques continues, cette option n'est pas disponible.  
  
7.  Si vous le souhaitez, spécifiez une valeur à utiliser comme **seuil cible** pour le comptage des prédictions comme étant précis. Cette valeur est exprimée en tant que probabilité, qui est un nombre compris entre 0 et 1, où 1 indique que la prédiction est garantie exacte, 0 signifie qu'il est peu probable que la prédiction soit correcte et .5 équivaut à une estimation aléatoire.  
  
     Si la colonne prévisible contient des données numériques continues, cette option n'est pas disponible.  
  
8.  Cliquez sur **Terminer**. Une nouvelle feuille de calcul est créée, nommée **validation croisée**.  
  
    > [!NOTE]  
    >  Microsoft Excel peut rester temporairement sans réponse pendant que le modèle est partitionné en replis et que chaque repli est testé.  
  
### <a name="requirements"></a>Spécifications  
 Pour créer un rapport de validation croisée, vous devez avoir déjà créé une structure d'exploration de données et des modèles connexes. L'Assistant fournit une boîte de dialogue pour vous aider à faire un choix parmi les structures et les modèles existants.  
  
 Si vous choisissez une structure d'exploration de données qui prend en charge plusieurs modèles d'exploration de données, et les modèles utilisent des attributs prévisibles différents, l'Assistant Validation croisée testera uniquement les modèles qui partagent le même attribut prévisible.  
  
 Si vous choisissez une structure qui prend en charge les modèles de clustering et d'autres types de modèles, les modèles de clustering ne seront pas testés.  
  
## <a name="understanding-cross-validation-results"></a>Présentation des résultats de la validation croisée  
 Les résultats de la validation croisée s’affichent dans une nouvelle feuille de calcul intitulée **rapport de validation \<croisée pour le nom d’attribut>**. La nouvelle feuille de calcul contient plusieurs sections : la première section est un résumé qui fournit des métadonnées importantes concernant le modèle testé, afin que vous puissiez déterminer à quel modèle ou à quelle structure les résultats sont destinés ;  
  
 la deuxième section dans le rapport fournit un résumé statistique qui indique la qualité du modèle d'origine. Dans ce résumé, les différences entre les modèles créés pour chaque pli sont analysées pour trois mesures principales : *erreur quadratique moyenne*, erreur d' *absolue moyenne*et *score du journal*. Ce sont les mesures statistiques standard qui sont utilisées non seulement dans l'exploration de données mais également dans la plupart des types d'analyse statistique.  
  
 Pour chacune de ces mesures, l'Assistant Validation croisée calcule l'écart moyen et type du modèle dans son ensemble. Cela vous indique le degré de cohérence du modèle lors d'une prédiction sur des sous-ensembles de données différents. Par exemple, si l'écart type est très important, il indique que les modèles créés pour chaque repli ont des résultats très différents, et que par conséquent l'apprentissage du modèle a pu porter trop fortement sur un groupe de données particulier et n'est peut-être pas applicable à d'autres ensembles de données.  
  
 La section suivante explique les mesures utilisées pour évaluer les modèles.  
  
### <a name="tests-and-measures"></a>Tests et mesures  
 Outre certaines informations de base sur le nombre de replis dans les données et le volume de données dans chaque repli, affiche un ensemble de mesures sur chaque modèle, classées par type de test. Par exemple, l'exactitude d'un modèle de clustering est évaluée par les différents tests que vous utiliseriez pour un modèle de prévision.  
  
 Le tableau suivant répertorie les tests et mesures, et explique la signification des mesures.  
  
#### <a name="aggregates-and-general-statistical-measures"></a>Agrégats et mesures statistiques générales  
 Les mesures d'agrégat fournies dans le rapport indiquent dans quelle mesure les replis que vous avez créés dans les données diffèrent les uns des autres.  
  
-   Écart type et moyen.  
  
-   Moyenne de l'écart par rapport à la moyenne d'une mesure spécifique, sur toutes les partitions d'un modèle.  
  
#### <a name="classification-passfail"></a>Classification : réussite/échec  
 Cette mesure est utilisée dans les modèles de classification lorsque vous ne spécifiez pas de valeur cible pour l'attribut prévisible. Par exemple, si vous créez un modèle qui prédit plusieurs possibilités, cette mesure vous renseigne sur la performance du modèle au niveau de la prédiction de toutes les valeurs possibles.  
  
 La réussite ou l’échec est calculé en calculant les cas qui remplissent les conditions suivantes : **réussite** si l’État prédit avec la probabilité la plus élevée est identique à l’état d’entrée et la probabilité est supérieure à la valeur que vous avez spécifiée pour le **seuil d’État**; Sinon, **échoue**.  
  
#### <a name="classification-true-or-false-positives-and-negatives"></a>Classification : vrais ou faux positifs et négatifs  
 Ce test est utilisé pour tous les modèles de classification qui ont une cible spécifiée. La mesure indique comment chaque cas est classé en réponse à ces questions : ce que le modèle a prédit, et ce qu'était le résultat réel.  
  
|Measure|Description|  
|-------------|-----------------|  
|Vrai positif|Nombre de cas qui remplissent ces conditions :<br /><br /> Le cas contient la valeur cible.<br /><br /> Le modèle a prédit que le cas contient la valeur cible.|  
|Faux positif|Nombre de cas qui remplissent ces conditions :<br /><br /> La valeur réelle est égale à la valeur cible.<br /><br /> Le modèle a prédit que le cas contient la valeur cible.|  
|Vrai négatif|Nombre de cas qui remplissent ces conditions :<br /><br /> Le cas ne contient pas la valeur cible.<br /><br /> Le modèle a prédit que le cas ne contient pas la valeur cible.|  
|Faux négatif|Nombre de cas qui remplissent ces conditions :<br /><br /> La valeur réelle n'est pas égale à la valeur cible.<br /><br /> Le modèle a prédit que le cas ne contient pas la valeur cible.|  
  
#### <a name="lift"></a>Finesse  
 L' *élévation* est une mesure associée à la probabilité. Si un résultat est plus probable lorsque vous utilisez le modèle que lorsque vous effectuez une estimation aléatoire, on dit que le modèle fournit une *élévation positive*. Toutefois, si le modèle effectue des prédictions moins probables que des chances aléatoires, le score d’élévation est *négatif*. Par conséquent, cette mesure indique le niveau d'amélioration qui peut être accompli en utilisant le modèle, où un score supérieur est meilleur.  
  
 La finesse est calculée en tant que rapport entre la probabilité de prédiction réelle et la probabilité marginale dans les scénarios de test.  
  
#### <a name="log-score"></a>Score du journal  
 Le *score du journal*, également appelé *score de probabilité du journal* pour la prédiction, représente le rapport entre deux probabilités, converti en échelle logarithmique. Étant donné que les probabilités sont représentées comme une fraction décimale, le score du journal est toujours un nombre négatif. Un score plus proche de 0 représente un meilleur score.  
  
 Alors que les scores bruts peuvent avoir des distributions très irrégulières ou asymétriques, un score de journal est semblable à un pourcentage.  
  
#### <a name="root-mean-square-error"></a>Erreur quadratique moyenne  
 L' *erreur quadratique moyenne* (RMSE) est une méthode standard dans les statistiques pour examiner le mode de comparaison des différents jeux de données, et lisser les différences qui peuvent être introduites par l’échelle des entrées.  
  
 L'erreur quadratique moyenne représente l'erreur moyenne de la valeur prédite par rapport à la valeur réelle. Elle est calculée en tant que racine carrée de l'erreur moyenne pour tous les cas de la partition, divisée par le nombre de cas dans la partition, en excluant les cas avec des valeurs manquantes pour les attributs cibles.  
  
#### <a name="mean-absolute-error"></a>Erreur d'absolue moyenne  
 L' *erreur absolue moyenne* est l’erreur moyenne de la valeur prédite à la valeur réelle. Elle est calculée en obtenant la somme absolue d'erreurs, et en recherchant la moyenne de ces erreurs.  
  
 Cette valeur vous aide à comprendre où se situent les scores par rapport à la moyenne.  
  
#### <a name="case-likelihood"></a>Probabilité de cas  
 Cette mesure est utilisée uniquement pour les modèles de clustering ; elle indique le degré de probabilité d'appartenance d'un nouveau cas à un cluster particulier.  
  
 Dans les modèles de clustering, il y a deux types d'appartenance au cluster, selon la méthode utilisée pour créer le modèle. Dans certains modèles, selon l'algorithme K-means, un nouveau cas est supposé appartenir à un seul cluster. Toutefois, l'algorithme de gestion de clusters Microsoftt utilise par défaut la méthode EM (Expectation Maximization), qui suppose qu'un nouveau cas peut potentiellement appartenir à tout cluster. Par conséquent, dans ces modèles qu'un cas peut avoir plusieurs valeurs `CaseLikelihood`, mais celui signalé par défaut est la probabilité du cas appartenant au cluster qui offre la meilleure correspondance pour le nouveau cas.  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des modèles et utilisation de modèles pour la prédiction &#40;compléments d’exploration de données pour Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
