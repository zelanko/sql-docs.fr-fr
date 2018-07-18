---
title: Exploration d’un modèle de réseau neuronal | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- mining model, neural network
- neural networks
- dependency network
ms.assetid: e4224cb7-115b-4889-ac07-03f096fb55fc
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ddfa179c57082eec38e14f0693cd707922f0812a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286365"
---
# <a name="browsing-a-neural-network-model"></a>Exploration d'un modèle MNN (Microsoft Neural Network)
  Quand vous ouvrez un modèle de réseau neuronal ou de régression logistique à l’aide de **Parcourir**, le modèle est affiché dans une visionneuse interactive semblable à la visionneuse de modèle de réseau neuronal dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La visionneuse permet d'explorer les corrélations et d'obtenir des informations sur les schémas du modèle et les données sous-jacentes.  
  
##  <a name="BKMK_Tabs"></a> Explorer le modèle  
 Les modèles basés sur les algorithmes de réseau neuronal ou de régression logistique de [!INCLUDE[msCoName](../includes/msconame-md.md)] sont similaires dans le sens où ils analysent des données comme un ensemble de connexions parmi les entrées et les sorties connues. La visionneuse **Parcourir** vous aide à explorer ces connexions, avec les contrôles suivants :  
  
-   [Variables](#BKMK_Variables)  
  
-   [Entrées](#BKMK_Inputs)  
  
-   [Sorties](#BKMK_Outputs)  
  
 Si vous souhaitez essayer cette visionneuse, vous pouvez créer un modèle à l’aide de [l’Assistant Classification &#40;compléments d’exploration de données pour Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md), puis utiliser l’option **Avancé** pour remplacer l’algorithme par Microsoft Logistic Regression dans la boîte de dialogue **Paramètres d’algorithme**.  
  
###  <a name="BKMK_Variables"></a> Variables  
 Le volet **Variables** affiche la liste des variables d’entrée par ordre de leur effet sur le modèle. Vous utilisez les contrôles **Entrée** et **Sortie** pour filtrer le modèle, ce qui affecte les variables qui sont affichées, ainsi que leur ordre.  
  
 Grâce à cette visionneuse, vous pouvez explorer les facteurs qui sont les plus importants pour déterminer si un client est plus susceptible d'appartenir à la catégorie des acheteurs de vélo ou à la catégorie des non-acheteurs.  
  
 ![Tester l’effet sur le résultat des attributs sélectionnés](media/dm13-neuralnet-agebuyer1.gif "tester l’effet sur le résultat des attributs sélectionnés")  
  
##### <a name="explore-variables"></a>Explorer les variables  
  
1.  Initialement, le volet **Variables** est trié par ordre des attributs les plus importants, en fonction des filtres actifs. La longueur de la barre indique l'intensité du facteur.  
  
     Dans l'exemple, vous pouvez voir que le revenu est le facteur le plus influent, suivi de la région. D'autre part, les clients possédant plusieurs voitures et les parents de plusieurs enfants sont bien moins susceptibles d'acheter un vélo.  
  
2.  Dans le volet **Variables**, cliquez sur l’en-tête de colonne **Attribut**.  
  
     En effectuant le tri sur l'attribut, vous pouvez voir les conteneurs qui ont été créés pour chacune des colonnes d'entrée. Les colonnes avec des valeurs discrètes, telles que la profession, sont placées dans un *conteneur* selon les valeurs littérales.  
  
3.  Notez les plages de valeurs qui ont été trouvées pour **Age** et **Income**.  
  
     Si certaines de vos colonnes d'entrée sont des nombres (autrement dit, la colonne de données entière est un type de données numériques continues), les nombres sont placés dans un compartiment, ou dans un conteneur, selon des plages discrètes.  
  
     Pour ce qui est du revenu, la colonne a été sous-divisée en regroupements tels que 78,4-154,06 (pour la plage de revenu la plus haute).  
  
     ![tri pour afficher la façon dont les variables ont été placées dans un conteneur](media/dm13-nn-bucketing-variables.gif "tri pour afficher la façon dont les variables ont été placées dans un conteneur")  
  
     Si vous souhaitez différents regroupements, utilisez l’outil [Réétiqueter &#40;compléments d’exploration de données SQL Server&#41;](relabel-sql-server-data-mining-add-ins.md) ou les fonctions Excel pour créer des catégories de revenu avant de générer le modèle.  
  
4.  Cliquez sur **Privilégie Oui** pour rétablir la vue par défaut du graphique.  
  
     Par défaut, la vue est triée selon la valeur de **Privilégie** pour la première valeur de résultat. Vous pouvez modifier les résultats qui sont attribués aux première et deuxième colonnes en choisissant une nouvelle valeur pour **Valeur 1** et **Valeur 2** dans **Sortie**.  
  
5.  Placez le pointeur de la souris sur la barre de couleur la plus élevée dans le graphique.  
  
     Une info-bulle apparaît. Elle comprend un score *d’importance*, une paire de scores de *probabilité* et une paire de valeurs de *finesse*.  
  
    -   **importance** est calculée dans l’intégralité du dataset et identifie l’attribut qui, compte tenu de toutes les entrées, est le plus corrélé avec le résultat cible. La visionneuse trie les valeurs dans le graphique par scores d'importance.  
  
    -   La **probabilité** est calculée pour chaque ensemble de paires attribut-valeur, pour les résultats cibles dans le jeu de données entier.  
  
    -   La **finesse** vous indique l’utilité de cette paire attribut-valeur particulière pour favoriser un résultat ou un autre.  
  
     Remarque : l'info-bulle contient les mêmes informations, quelle que soit la colonne où vous positionnez la souris.  
  
 [Retour au début](#BKMK_Tabs)  
  
###  <a name="BKMK_Inputs"></a> Entrées  
 Le volet **Entrées** vous permet de choisir un ensemble d’entrées et de l’appliquer en tant que filtre au modèle, ce qui vous permet de voir l’impact de ces choix sur les résultats, en fonction des données d’apprentissage  
  
##### <a name="explore-inputs"></a>Explorer les entrées  
  
1.  Supposez que vous vouliez cibler un groupe particulier et voir les facteurs qui influent le plus sur la décision d'achat dans ce groupe.  
  
     Dans le **entrée** volet, cliquez sur le  **\<tous les >** cellule sous **attribut**, puis sélectionnez **âge**.  
  
     Pour **Valeur**, sélectionnez la catégorie correspondant à la tranche d’âge des plus jeunes.  
  
2.  Notez que même lorsque vous filtrez sur un groupe d'âges particulier, la zone Pacifique est proche du haut de la liste. Cela s'explique par le fait que les clients de la zone Pacifique sont bien plus susceptibles d'acheter un vélo que les clients dans d'autres régions du monde.  
  
     Dans la mesure où la région ne constitue pas un critère sur lequel vous pouvez influer, vous pouvez à nouveau modifier les entrées pour supprimer cette variable des facteurs à prendre en compte et afficher d'autres facteurs.  
  
     Dans le volet **Entrée**, cliquez sur la cellule vide sous **Age** puis sélectionnez **Region**.  
  
     Pour **Valeur**, sélectionnez **Europe**.  
  
3.  Continuez à ajouter des filtres d'entrée pour vous concentrer sur un groupe d'intérêt spécifique.  
  
     Par exemple, pour l’attribut d’entrée, ajoutez **Gender**, puis sélectionnez **Female** comme valeur.  
  
     ![Tester l’effet sur le résultat des attributs sélectionnés](media/dm13-neuralnet-agebuyer2.gif "tester l’effet sur le résultat des attributs sélectionnés")  
  
     Notez le changement de la liste des variables. Maintenant, **Income** est la variable qui est la plus importante lors de la prédiction du résultat cible.  
  
     L'ordre dans lequel vous appliquez les filtres d'entrée n'affecte pas les résultats.  
  
 [Retour au début](#BKMK_Tabs)  
  
###  <a name="BKMK_Outputs"></a> Sorties  
 Dans le volet **Outputs**, vous pouvez choisir le résultat qui vous intéresse. Les réseaux neuronaux vous permettent de spécifier autant de colonnes de résultats que vous le souhaitez, bien que l'ajout de sorties supplémentaires ajoute à la complexité du modèle et puisse nécessiter un temps de traitement beaucoup plus long.  
  
 Pour comparer deux sorties, elles doivent avoir été désignées comme colonnes **Prédire** ou **Prédire uniquement**.  
  
##### <a name="explore-outputs"></a>Explorer les sorties  
  
1.  Utilisez la liste **Attribut de sortie** pour sélectionner un attribut.  
  
2.  Sélectionnez deux résultats des listes Valeur 1 et Valeur 2. Ces deux états de l’attribut de sortie seront comparés dans le volet **Variables** .  
  
 [Retour au début](#BKMK_Tabs)  
  
## <a name="more-about-neural-network-models"></a>En savoir plus sur les modèles de réseau neuronal  
 Les informations de la visionneuse sont récupérées du serveur à l'aide d'une procédure stockée spécifique à ce type de modèle : System.Microsoft.AnalysisServices.System.DataMining.NeuralNet.GetAttributeScores.  
  
 Si vous souhaitez créer un modèle comprenant de nombreux attributs prédictibles à l’aide des compléments, utilisez les options de modélisation **Avancé**.  
  
 Pour plus d’informations, consultez [Créer une structure d’exploration de données &#40;compléments d’exploration de données SQL Server&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) et [Ajouter un modèle à une structure &#40;compléments d’exploration de données pour Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration des modèles dans Excel &#40;compléments d’exploration de données SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
