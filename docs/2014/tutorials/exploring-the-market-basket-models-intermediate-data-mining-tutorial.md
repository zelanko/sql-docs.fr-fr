---
title: Exploration des modèles de panier d’exploitation (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: da1c9cb7-6c32-4b9b-96ec-ecea772aeb77
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8a7b2f97cbda0594698c6cbaa68019a6493f1e74
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63224607"
---
# <a name="exploring-the-market-basket-models-intermediate-data-mining-tutorial"></a>Exploration des modèles d'analyse de panier (Didacticiel intermédiaire sur l'exploration de données)
  Maintenant que vous avez créé le `Association` modèle, vous pouvez l’Explorer à l’aide [!INCLUDE[msCoName](../includes/msconame-md.md)] de la visionneuse d’associations dans l’onglet **visionneuse de modèle d’exploration** de données du concepteur d’exploration de données. Ce didacticiel vous guide dans l'utilisation de la visionneuse pour explorer les relations entre des éléments. La visionneuse vous aide à consulter d'un coup d'œil les produits qui tendent à apparaître ensemble et avoir une idée générale des nouvelles tendances.  
  
 La [!INCLUDE[msCoName](../includes/msconame-md.md)] visionneuse d’associations contient trois onglets : **règles**, **jeux d’éléments**et **réseau de dépendances**. Comme chaque onglet révèle une vue légèrement différente des données, lorsque vous explorez un modèle, vous basculez en général entre les différents volets plusieurs fois pour obtenir des éclaircissements.  
  
-   [Onglet réseau de dépendances](#bkmk_DepNet)  
  
-   [Onglet Jeux d’éléments](#bkmk_Itemsets)  
  
-   [Onglet Règles](#bkmk_Rules)  
  
-   [Vue de contenu générique](#bkmk_ContentViewer)  
  
 Pour ce didacticiel, vous allez démarrer sous l’onglet **réseau de dépendances** , puis utiliser l’onglet **règles** et l’onglet **jeux d’éléments** pour approfondir votre compréhension des relations révélées dans la visionneuse. Vous allez également utiliser la **visionneuse de l’arborescence de contenu générique Microsoft** pour récupérer des statistiques détaillées pour des règles individuelles ou des jeux d’éléments.  
  
##  <a name="dependency-network-tab"></a><a name="bkmk_DepNet"></a>Onglet réseau de dépendances  
 Avec l’onglet **réseau de dépendances** , vous pouvez examiner l’interaction des différents éléments dans le modèle. Chaque nœud dans la visionneuse représente un élément et les lignes entre les éléments représentent des règles. En sélectionnant un nœud, vous pouvez voir les autres nœuds qui prédisent l'élément sélectionné, ou les éléments prédits par ce dernier. Parfois, il existe une association bidirectionnelle entre des éléments, ce qui signifie qu'ils apparaissent souvent dans la même transaction. Vous pouvez vous reporter à la légende de couleur en bas d'onglet pour déterminer la direction de l'association.  
  
 Une ligne qui connecte deux éléments indique qu'il est probable que ces éléments apparaissent ensemble dans une transaction. En d'autres termes, il est probable que les clients achètent ces éléments ensemble. Le curseur est associé à la probabilité de la règle. Déplacez le curseur vers le haut ou le bas pour éliminer les associations faibles, c'est à dire les règles avec une faible probabilité.  
  
 Le graphique du réseau de dépendances affiche les règles par paire, qui peuvent être représentées logiquement comme un->B, ce qui signifie que si le produit A est acheté, le produit B est probablement. Le graphique ne peut pas afficher les règles du type AB->C. Si vous déplacez le curseur pour afficher toutes les règles sans toutefois pouvoir afficher une ligne dans le graphique, cela signifie qu'aucune règle par couple ne correspond aux critères des paramètres de l'algorithme.  
  
 Vous pouvez rechercher également des nœuds par nom en tapant les premières lettres du nom d'attribut. Pour plus d’informations, consultez [Boîte de dialogue Rechercher un nœud &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/find-node-dialog-box-mining-model-viewer.md).  
  
#### <a name="to-open-the-association-mode-in-the-microsoft-assocaition-rules-viewer"></a>Pour ouvrir le mode Association dans la Visionneuse de l'algorithme MAR (Microsoft Association Rules)  
  
1.  Dans **Explorateur de solutions**, double-cliquez sur la structure d’association.  
  
2.  Dans le Concepteur d'exploration de données, cliquez sur l'onglet **Visionneuse de modèle d'exploration de données** .  
  
3.  Sélectionnez Association dans la liste déroulante modèle d' **exploration** de données.  
  
#### <a name="to-navigate-the-dependency-graph-and-locate-specific-nodes"></a>Pour naviguer dans le graphique des dépendances et localiser des nœuds spécifiques  
  
1.  Dans l’onglet **visionneuse de modèle d’exploration de données** , cliquez sur l’onglet réseau de **dépendances** .  
  
2.  Cliquez plusieurs fois sur **Zoom** , jusqu’à ce que vous puissiez facilement afficher les étiquettes de chaque nœud.  
  
     Par défaut, le graphique s'affiche avec tous les nœuds visibles. Dans un modèle complexe, il peut y avoir de nombreux nœuds, ce qui réduit la taille de chaque nœud.  
  
3.  Cliquez sur **+** le signe dans le coin inférieur droit de la visionneuse et maintenez le bouton de la souris enfoncé pour effectuer un panoramique autour du graphique.  
  
4.  Sur le côté gauche de la visionneuse, faites glisser le curseur vers le bas, en le déplaçant de **tous les liens** (valeur par défaut) vers le bas du contrôle Slider.  
  
5.  La visionneuse met à jour le graphique pour n'afficher désormais que l'association la plus forte entre les éléments Touring Tire (Pneu pour vélo de tourisme) et Touring Tire Tube (chambre à air pour vélo de tourisme).  
  
6.  Cliquez sur le nœud intitulé **cyclotourisme pneu tube = existing**.  
  
     Le graphique est mis à jour pour mettre en surbrillance uniquement les éléments ayant une forte relation avec cet élément. Notez la direction de la flèche entre les deux éléments.  
  
7.  Sur le côté gauche de la visionneuse, faites glisser encore le curseur vers le haut, en le déplaçant du bas vers le milieu.  
  
     Notez les modifications dans la flèche qui connecte les deux éléments.  
  
8.  Sélectionnez **afficher le nom de l’attribut uniquement** dans la liste déroulante en haut du volet réseau de dépendances.  
  
     Les intitulés de texte dans le graphique sont mis à jour pour afficher uniquement le nom de modèle.  
  
 [Retour au début](#bkmk_DepNet)  
  
##  <a name="itemsets-tab"></a><a name="bkmk_Itemsets"></a>Onglet Jeux d’éléments  
 Ensuite, vous approfondirez vos connaissances des règles et des jeux d'éléments générés par le modèle pour les produits Touring Tire et Touring Tire Tube. L’onglet **jeux d’éléments** affiche trois informations importantes relatives au jeux d’éléments que l' [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme d’association Découvre :  
  
-   **Prise en charge :** Nombre de transactions dans lesquelles le jeu d’éléments se produit.  
  
-   **Taille :** Nombre d’éléments dans le jeu d’éléments.  
  
-   **Éléments :** Liste des éléments inclus dans chaque jeu d’éléments.  
  
 En fonction de la manière dont les paramètres d'algorithme sont définis, l'algorithme peut générer un grand nombre de jeux d'éléments. Chaque jeu d'éléments retourné dans la visionneuse représente des transactions dans lesquelles l'élément a été vendu. En utilisant les contrôles en haut de l’onglet **jeux d’éléments** , vous pouvez filtrer la visionneuse pour afficher uniquement les jeux d’éléments qui contiennent la prise en charge minimale spécifiée et la taille de jeu d’éléments.  
  
 Si vous utilisez un modèle d'exploration de données différent et qu'aucun jeu d'éléments n'est répertorié, cela signifie qu'aucun jeu d'éléments n'a répondu aux critères des paramètres d'algorithme. Dans ce scénario, vous pouvez modifier les paramètres d'algorithme pour autoriser les jeux d'éléments dont la prise en charge est plus faible.  
  
#### <a name="to-filter-the-itemsets-that-are-shown-in-the-viewer-by-name"></a>Pour filtrer par nom les jeux d'éléments affichés dans la visionneuse  
  
1.  Cliquez sur l’onglet **jeux d’éléments** de la visionneuse.  
  
2.  Dans la zone **filtre jeu d’éléments** , tapez `Touring Tire`, puis cliquez à l’extérieur de la zone.  
  
     Le filtre retourne tous les éléments qui contiennent cette chaîne.  
  
3.  Dans la liste **Afficher** , sélectionnez **afficher le nom de l’attribut uniquement**.  
  
4.  Activez la case à cocher **afficher le nom long** .  
  
     La liste des jeux d'éléments est mise à jour pour afficher uniquement les jeux d'éléments qui contiennent la chaîne Touring Tire. Le nom long du jeu d'éléments inclut le nom de la table qui contient l'attribut et la valeur pour chaque élément.  
  
5.  Désactivez la case à cocher **afficher le nom long** .  
  
     La liste des jeux d'éléments est mise à jour pour afficher uniquement le nom court.  
  
 Les valeurs dans la colonne **support** indiquent le nombre de transactions pour chaque jeu d’éléments. Une transaction pour un jeu d'éléments signifie un achat qui comprend tous les éléments dans le jeu d'éléments.  
  
 Par défaut, la visionneuse répertorie les jeux d'éléments par ordre décroissant de prise en charge. Vous pouvez cliquer sur les en-têtes de colonne pour trier par une colonne différente, telle que la taille ou le nom du jeu d'éléments. Si vous souhaitez en savoir plus sur les transactions individuelles incluses dans un jeu d'éléments, vous pouvez extraire les cas individuels à partir des jeux d'éléments. Les colonnes de structure dans les résultats d'extraction sont le niveau de revenu du client et l'ID du client qui n'étaient pas été utilisés dans le modèle.  
  
#### <a name="to-view-details-for-an-itemset"></a>Pour consulter les détails d'un jeu d'éléments  
  
1.  Dans la liste des jeux d’éléments, cliquez sur l’en-tête de colonne **jeu d’éléments** pour trier par nom.  
  
2.  Localisez l’élément `Touring Tire` (sans deuxième élément).  
  
3.  Cliquez avec le bouton droit sur `Touring Tire`l’élément,, sélectionnez **extraire**, puis sélectionnez **colonnes de structure et de modèle**.  
  
     La boîte de dialogue **extraire** affiche les transactions individuelles utilisées comme prise en charge pour ce jeu d’éléments.  
  
4.  Développez la table imbriquée, vAssocSeqLineItems, pour consulter la liste réelle des achats dans la transaction.  
  
#### <a name="to-filter-itemsets-by-support-or-size"></a>Pour filtrer les jeux d'éléments par prise en charge ou taille  
  
1.  Effacez tout texte qui peut figurer dans la zone **filtrer le jeu d’éléments** . Vous ne pouvez pas utiliser un filtre de texte avec un filtre numérique.  
  
2.  Dans la zone **prise en charge minimale** , tapez 100, puis cliquez sur l’arrière-plan de la visionneuse.  
  
     La liste des jeux d'éléments est mise à jour pour afficher uniquement les jeux d'éléments avec une prise en charge d'au moins 100.  
  
 [Retour au début](#bkmk_DepNet)  
  
##  <a name="rules-tab"></a><a name="bkmk_Rules"></a>Onglet Règles  
 L’onglet **règles** affiche les informations suivantes relatives aux règles trouvées par l’algorithme.  
  
-   **Probabilité :** *Probabilité* d’une règle, définie comme la probabilité de l’élément de droite en fonction de l’élément de la partie gauche.  
  
-   **Importance :** Mesure de l’utilité d’une règle. Une valeur supérieure signifie une meilleure règle.  
  
     L'importance est indiquée pour vous aider à mesurer l'utilité d'une règle, car se baser uniquement sur la probabilité peut porter à confusion. Par exemple, si chaque transaction contient une bouteille d'eau-- la bouteille d'eau est peut-être ajoutée automatiquement au chariot de chaque client dans le cadre d'une promotion--le modèle peut créer une règle qui prédit que la bouteille d'eau a une probabilité de 1. En tenant compte de la probabilité uniquement, cette règle est exacte, mais elle ne fournit pas d'informations utiles.  
  
-   **Règle :** Définition de la règle. Pour un modèle d'analyse de panier, une règle décrit une combinaison spécifique d'éléments.  
  
 Chaque règle peut être utilisée pour prévoir la présence d'un élément dans une transaction en se basant sur la présence d'autres éléments. Comme dans l’onglet **jeux d’éléments** , vous pouvez filtrer les règles pour afficher uniquement les règles les plus intéressantes. Si vous utilisez un modèle d'exploration de données qui n'a pas de règles, vous pouvez modifier les paramètres d'algorithme pour abaisser le seuil de probabilité des règles.  
  
#### <a name="to-see-only-rules-that-include-the-mountain-200-bicycle"></a>Pour n'afficher que les règles qui incluent le vélo Mountain-200  
  
1.  Dans l’onglet **visionneuse de modèle d’exploration de données** , cliquez sur l’onglet **règles** .  
  
2.  Dans la zone **filtrer la règle** , `Mountain-200`entrez.  
  
     Désactivez la case à cocher **afficher le nom long** .  
  
3.  Dans la liste **Afficher** , sélectionnez **afficher le nom de l’attribut uniquement**.  
  
     La visionneuse affiche alors uniquement les règles qui contiennent les mots «`Mountain-200`». La probabilité de la règle vous indique la probabilité que, lorsque quelqu’un achète un `Mountain-200` vélo, cette personne achète également l’autre produit mentionné.  
  
 Les règles sont classées par probabilité en ordre décroissant, mais vous pouvez cliquer sur les en-têtes de colonnes pour modifier l'ordre de tri. Pour en savoir plus sur une règle particulière, vous pouvez utiliser l'extraction pour consulter les cas de prise en charge.  
  
#### <a name="to-view-cases-that-support-a-particular-rule"></a>Pour consulter des cas qui prennent en charge une règle particulière  
  
1.  Dans l’onglet **règles** , cliquez avec le bouton droit sur la règle que vous souhaitez afficher.  
  
2.  Sélectionnez **extraire**, puis sélectionnez colonnes de **modèle uniquement**ou **colonnes de structure et de modèle**.  
  
     La boîte de dialogue **extraire** fournit un résumé de la règle en haut du volet, ainsi qu’une liste de tous les cas utilisés comme données de prise en charge pour la règle.  
  
 [Retour au début](#bkmk_DepNet)  
  
##  <a name="generic-content-tree-viewer"></a><a name="bkmk_ContentViewer"></a>Visionneuse de l’arborescence de contenu générique  
 Cette visionneuse peut être utilisée pour tous les modèles, quels que soient l'algorithme ou le type de modèle. La **visionneuse de l’arborescence de contenu générique Microsoft** est disponible dans la liste déroulante **visionneuse** .  
  
 Une arborescence de contenu est une représentation d'un modèle d'exploration de données sous forme de série de nœuds, où chaque nœud représente ce qui a été appris sur certains sous-ensembles des données. Le nœud peut contenir un modèle, un ensemble de règles, un cluster ou la définition d'une plage de dates qui partagent certaines caractéristiques. Le contenu exact du nœud diffère selon l'algorithme et le type de l'attribut prédictible, mais la représentation générale du contenu reste la même. Vous pouvez développer chaque nœud pour voir des informations de plus en plus détaillées et copier le contenu de n'importe quel nœud vers le Presse-papiers.  
  
#### <a name="to-view-details-about-the-rule-by-using-the-content-viewer"></a>Pour consulter des détails sur la règle en utilisant la visionneuse de contenu  
  
1.  Dans l’onglet **visionneuse de modèle d’exploration de données** , sélectionnez Visionneuse de l’arborescence de **contenu générique Microsoft** dans la liste des **visionneuses** .  
  
2.  Dans le volet Légende du nœud, faites défiler vers le bas de la liste et cliquez sur le dernier nœud.  
  
     La visionneuse affiche d'abord les jeux d'éléments et les règles ensuite, mais elle ne les groupe pas. La méthode la plus simple pour rechercher un nœud spécifique est de créer une requête de contenu. Pour plus d’informations, consultez [Exemples de requête de modèle d’association](../../2014/analysis-services/data-mining/association-model-query-examples.md).  
  
3.  Dans le volet Détails du nœud, examinez la valeur pour NODE_TYPE et NODE_DESCRIPTION.  
  
     Un type de nœud de 8 est une règle, et un type de nœud de 7 est un jeu d'éléments. Pour une règle, la valeur NODE_DESCRIPTION vous indique les conditions qui composent la règle. Pour un jeu d'éléments, la valeur NODE_DESCRIPTION vous indique les éléments inclus dans le jeu d'éléments.  
  
 Vous pouvez créer également une requête de contenu pour obtenir des statistiques détaillées sur les règles. Pour plus d’informations sur le contenu du modèle d’exploration de données et son interprétation, consultez [Mining Model Content for Association models &#40;Analysis Services-data mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).  
  
 [Retour au début](#bkmk_DepNet)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Filtrage d’une table imbriquée dans un modèle d’exploration de données &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Leçon 3 : création d’un scénario de panier de marché &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)   
 [Leçon 4 : génération d’un scénario Sequence Clustering &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)   
 [Algorithme d’association Microsoft](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)   
 [Références techniques relatives à l’algorithme Microsoft Association](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)  
  
  
