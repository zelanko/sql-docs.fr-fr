---
title: Modèle d’arbre de décision de navigation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- tree viewer
- mining model, decision tree
- decision tree [data mining]
- dependency network
ms.assetid: 6b3dd1ae-caff-41c3-817b-802dc020ff88
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e9e1ccaf9e000779485be93e476f9114817529a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137049"
---
# <a name="browsing-a-decision-trees-model"></a>Exploration d'un modèle Arbre de décision
  Lorsque vous ouvrez un modèle de classification avec **Parcourir**, le modèle est affiché dans une visionneuse d’arbre de décision interactive semblable à la [!INCLUDE[msCoName](../includes/msconame-md.md)] visionneuse d’arbres de décision dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La visionneuse affiche les résultats de la classification sous la forme d'un graphique qui est conçu pour mettre en évidence les critères qui différencient un groupe de données d'un autre. Vous pouvez également explorer des sous-ensembles individuels de l'arborescence et récupérer les données sous-jacentes.  
  
##  <a name="bkmk_Top"></a> Explorer le modèle  
 Les modèles fondés sur l'algorithme MDT comportent un certain nombre d'informations intéressantes à explorer. Le **Parcourir** fenêtre inclut les onglets et volets pour vous aider à apprendre les schémas et de prédire l’utilisation du graphique des résultats suivants :  
  
-   [Arbre de décision](#BKMK_DecisionTree)  
  
-   [Réseau de dépendances](#BKMK_DNetwork)  
  
 Pour expérimenter avec un modèle d'arbre de décision, vous pouvez utiliser les exemples de données sous l'onglet Données d'apprentissage (ou Données source) du classeur Exemples de données, puis créer un modèle d'arbre de décision en utilisant Bike Buyer comme attribut prédictible.  
  
###  <a name="BKMK_DecisionTree"></a> Arbre de décision  
 Cette vue est conçue pour vous aider à comprendre et à explorer les facteurs qui mènent à un résultat.  
  
 Le graphique d'arbre de décision peut être lu de gauche à droite, comme suit :  
  
-   Les rectangles, sont appelés *nœuds*, contiennent des sous-ensembles des données. L'étiquette sur le nœud vous indique les caractéristiques de définition de ce sous-ensemble.  
  
-   Le nœud à l’extrême gauche, intitulé **tous les**, représente le jeu de données complet. Tous les nœuds suivants représentent des sous-ensembles des données.  
  
-   Un arbre de décision contient de nombreux *fractionne*, ou les emplacements où les données divergent en plusieurs jeux en fonction d’attributs.  
  
     Par exemple, le premier fractionnement de l'exemple de modèle divise le dataset en trois groupes d'âges.  
  
-   Le fractionnement immédiatement après le **tous les** nœud est le plus important, car il indique la condition principale qui divise ce jeu de données.  
  
     Des fractionnements supplémentaires apparaissent à droite. Ainsi, lors de l'analyse de différents segments de l'arborescence, vous pouvez découvrir les attributs qui influaient le plus sur le comportement d'achat.  
  
 ![Réseau de dépendances pour un modèle d’association](media/dm13-dec-tree-split-definition.gif "réseau de dépendances pour un modèle d’association")  
  
 Grâce à ces informations, vous pouvez cibler une campagne marketing sur les clients qui ont peut-être simplement besoin d'être encouragés pour effectuer un achat.  
  
##### <a name="explore-the-decision-tree"></a>Explorer l'arbre de décision  
  
1.  Cliquez sur le **tous les** nœud, puis examinez le **légende d’exploration de données**.  
  
     Elle affiche le nombre exact de cas dans le jeu de données d'apprentissage, ainsi qu'une décomposition des résultats.  
  
     Vous pouvez afficher les mêmes informations dans une info-bulle si vous maintenez le pointeur de la souris au niveau d'un nœud.  
  
2.  Cliquez sur les signes plus et moins en regard de chaque nœud afin de développer ou de réduire l'arborescence.  
  
     Vous pouvez également utiliser le **afficher le niveau** curseur pour développer ou réduire l’arborescence.  
  
3.  Vous avez remarqué que certains nœuds sont plus foncés que d'autres ?  
  
     Par défaut, **Population** est utilisé en tant que la variable d’ombrage, ce qui signifie que l’intensité de la couleur vous montre les nœuds qui ont le plus prise en charge.  
  
     Par conséquent, le nœud situé le plus à gauche est le plus foncé, car il contient le dataset entier.  
  
4.  Modifiez la valeur de **arrière-plan** de **tous les cas** à **Oui**.  
  
     ![variation graphique d’arbre de décision pour mettre en surbrillance les acheteurs](media/dm13-dectreeshadedbuyer.gif "modification graphique d’arbre de décision pour mettre en surbrillance les acheteurs")  
  
5.  Maintenant, l'intensité de la couleur vous indique le nombre de clients dans chaque nœud qui ont acheté un vélo, ce qui correspond au comportement qui vous intéresse.  
  
     Notez les barres de couleur dans chaque nœud. Il s'agit d'un histogramme qui montre la distribution des résultats dans ce sous-ensemble de données. Par exemple, dans l’arbre de décision exemple Bike Buyer, la barre de couleur montre la proportion de clients qui ont acheté des vélos (valeurs Oui) et celles qui n’ont pas (aucune valeur). Pour obtenir les valeurs exactes, vous pouvez cliquer sur le nœud et afficher le **légende d’exploration de données**.  
  
6.  En suivant le graphique, vous pouvez voir comment chaque sous-ensemble de données est à son tour décomposé en groupes plus petits, ainsi que les attributs qui sont le plus utile lors de la prédiction d'un résultat.  
  
     Il suffit d'observer l'intensité de l'ombrage pour pouvoir se concentrer sur quelques groupes d'intérêt et obtenir des données plus détaillées à leur sujet pour effectuer une comparaison. Par exemple, ces groupes présentent une probabilité relativement élevée d'acheter des vélos :  
  
    -   Âge > = 32 et \< 53 et Yearly Income > = 26000 et enfants = 0  
  
         Total des cas : 1150  
  
         Probabilité d’acheter des vélos : 18 %  
  
    -   Âge > = 32 et \< 53 et Yearly Income > = 26000 et enfants ne pas = 0 et Marital état = 'Single'  
  
         Total des cas : 402  
  
         Probabilité d'acheter un vélo : 16 %  
  
7.  Modifiez la valeur de **arrière-plan** de **Oui** à **non** et voir comment le graphique change.  
  
     ![Réseau de dépendances pour un modèle d’association](media/dm13-dec-tree-background-no.gif "réseau de dépendances pour un modèle d’association")  
  
 **Conseils**  
  
-   Si vos données peuvent être divisées en plusieurs séries, un modèle différent est créé pour chaque jeu de données à modéliser.  
  
-   Dans le modèle Exemples de données, il n'existe qu'un résultat prédictible, Bike Buyer. Mais supposez que vous disposiez d'informations indiquant si le client a acheté un plan de services et que vous souhaitiez prédire ces données également. Dans ce cas, vous placeriez ces données dans une colonne distincte et vous incluriez deux attributs prédictibles au modèle.  
  
     Cliquez sur le **histogramme** option, dans le coin supérieur gauche du volet de l’arbre de décision, pour modifier le nombre maximal d’États qui peuvent apparaître dans les histogrammes dans l’arborescence. Cette option est utile si l'attribut prévisible possède de nombreux états. Les états s'affichent dans un histogramme par ordre de fréquence de gauche à droite.  
  
-   Vous pouvez également utiliser les options sur la **arbre de décision** onglet affectent le mode d’affichage de l’arborescence, en zoom avant ou arrière, ou la taille du graphique pour ajuster à la fenêtre.  
  
-   Utilisez **Expansion par défaut** pour définir le nombre de niveaux par défaut affichés pour tous les arbres du modèle.  
  
-   Sélectionnez **afficher le nom long** pour afficher le nom complet de l’attribut, y compris la source de données. Les noms longs et les noms courts sont identiques, sauf si vos cas proviennent d'une source de données différente des attributs de chaque cas.  
  
 [Retour au début](#bkmk_Top)  
  
###  <a name="BKMK_DNetwork"></a> Réseau de dépendances  
 Le **réseau de dépendances** vue affiche les connexions entre les attributs d’entrée et les attributs prédictibles du modèle.  
  
1.  Cliquez et faites glisser le curseur à gauche de la visionneuse  
  
     Dans la position supérieure, toutes les connexions sont affichées. Lorsque vous faites glisser le curseur vers le bas, la visionneuse affiche uniquement les liens les plus forts.  
  
2.  Cliquez maintenant sur le nœud Bike Buyer (Acheteur de vélo).  
  
     ![Vue du réseau de dépendances pour les arbres de décision](media/dm13-dectree-depnet.gif "vue du réseau de dépendances pour les arbres de décision")  
  
     Lorsque vous sélectionnez un nœud, la visionneuse met en surbrillance les dépendances propres à ce nœud. Dans ce cas, la visionneuse met en surbrillance chaque nœud qui aide à prédire le résultat.  
  
3.  Si la visionneuse contient un grand nombre de nœuds, vous pouvez rechercher des nœuds spécifiques à l’aide de la **rechercher un nœud** bouton. En cliquant sur **Rechercher un nœud** , vous ouvrez la boîte de dialogue **Rechercher un nœud** dans laquelle vous pouvez utiliser un filtre pour rechercher et sélectionner des nœuds spécifiques.  
  
4.  La légende en bas de la visionneuse associe des codes de couleur au type de dépendance apparaissant dans le graphique. Par exemple, lorsque vous sélectionnez un nœud prévisible, le nœud prévisible est surligné en turquoise et les nœuds permettant de prédire le nœud sélectionné sont surlignés en orange.  
  
 [Retour au début](#bkmk_Top)  
  
### <a name="drill-through-to-underlying-data"></a>Explorer les données sous-jacentes  
 Plusieurs types de modèles prennent en charge la possibilité de *extraction* à partir du modèle de données de cas sous-jacentes. Cela peut se révéler très utile si vous voulez contacter les clients dans un segment particulier ou extraire les données pour poursuivre l'analyse.  
  
##### <a name="get-case-data"></a>Obtenir les données de cas  
  
1.  Cliquez avec le bouton droit sur le nœud de l'arborescence qui contient les données désirées, puis sélectionnez l'une de ces options :  
  
    -   **Extraire le modèle**. Cette option permet d'obtenir les cas qui appartiennent au nœud sélectionné et de les enregistrer dans un tableau Excel. Vous obtenez uniquement les colonnes de données ayant été réellement utilisées lors de la génération du modèle.  
  
    -   **Extraction des colonnes de Structure**. Cette option permet d'obtenir les cas qui appartiennent au nœud sélectionné et de les enregistrer dans un tableau Excel. Vous obtenez toutes les informations qui étaient disponibles dans les données sous-jacentes lorsque vous les avez générées, même celles d'une colonne qui n'ont pas été utilisées dans le modèle. Par exemple, vous avez peut-être exclu l'adresse et le code postal du client car ces champs ne sont pas utiles pour l'analyse, mais vous les avez laissés dans la structure.  
  
     Revenez dans Excel pour afficher vos données. La visionneuse Parcourir exécute une requête, enregistre les données dans un tableau dans une nouvelle feuille de calcul, puis étiquette les résultats.  
  
     ![résultats de l’extraction sont enregistrés dans Excel](media/dm13-dectree-drillthroughresults.gif "résultats de l’extraction sont enregistrés dans Excel")  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration des modèles dans Excel &#40;compléments d’exploration de données SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
