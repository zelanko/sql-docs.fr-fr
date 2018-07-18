---
title: Exploration d’un modèle de Clustering | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- clustering [data mining]
- mining model, clustering
ms.assetid: 7f3f0949-d791-403a-88e2-54cb1a803dae
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 006decb2e339c07252cc0dbfeaee60962db36e0f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37212169"
---
# <a name="browsing-a-clustering-model"></a>Exploration d'un modèle de clustering
  Lorsque vous ouvrez un modèle de clustering avec **Parcourir**, le modèle est affiché dans une visionneuse interactive semblable à la visionneuse de clustering dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Cette visionneuse vous aide à explorer les clusters qui ont été créés et à comprendre les caractéristiques de cluster. Vous pouvez également comparer des segments individuels avec d'autres segments ou avec la population, et mettre en évidence les différences.  
  
##  <a name="BKMK_Tabs"></a> Explorer le modèle  
 Le **Parcourir** fenêtre inclut les outils suivants pour vous aider à comprendre votre modèle de clustering et Explorer les attributs des groupes de données sous-jacente :  
  
-   [Diagramme de cluster](#BKMK_ClusterDiagram)  
  
-   [Profils du cluster](#BKMK_ClusterProfiles)  
  
-   [Caractéristiques du cluster](#BKMK_ClusterCharacteristics)  
  
-   [Discrimination de cluster](#BKMK_ClusterDiscrimination)  
  
 Pour faire des essais avec un modèle de clustering, vous pouvez utiliser les exemples de données sur l’onglet d’apprentissage de l’exemple de classeur de données et créez un modèle de clustering avec [Assistant Cluster &#40;des compléments d’exploration de données pour Excel&#41; ](cluster-wizard-data-mining-add-ins-for-excel.md) et toutes les valeurs par défaut .  
  
###  <a name="BKMK_ClusterDiagram"></a> Diagramme de cluster  
 Le **diagramme de Cluster** onglet affiche tous les clusters qui se trouvent dans un modèle d’exploration de données. Vous pouvez voir ici le nombre important de regroupements différents qui ont été détectés dans votre jeu de données, ainsi que leur proximité les uns par rapport aux autres.  
  
##### <a name="explore-the-cluster-diagram"></a>Explorer le diagramme de cluster  
  
1.  Cliquez sur Cluster 1 dans le diagramme.  
  
     Notez comment les lignes grises reliant tous les clusters changent pour mettre en surbrillance en bleu vif les lignes menant au cluster sélectionné.  
  
     ![introduction du diagramme de cluster](media/dm13-cluster-diagram-intro.gif "introduction du diagramme de cluster")  
  
     L'intensité de la ligne reliant un cluster à un autre représente le niveau de similarité des clusters. Si l'ombrage est clair ou inexistant, les clusters ne sont pas très similaires. Plus la ligne est sombre, plus la similarité entre les deux clusters est importante.  
  
2.  Cliquez et faites glisser le curseur à gauche du diagramme de cluster pour modifier le nombre de lignes affichées par la visionneuse.  
  
     Lorsque vous faites glisser le curseur vers le bas, seuls les liens les plus forts entre les clusters sont affichés. Cela vous aide à vous concentrer sur les groupes associés.  
  
3.  Notez que le **Variable d’ombrage** contrôle dans le coin supérieur droit de la **diagramme de Cluster** fenêtre.  
  
     Par défaut, il est défini sur **Population**. Cela signifie que les clusters les plus foncés bénéficient d'une meilleure prise en charge.  
  
4.  Placez le curseur de la souris au niveau d'un cluster.  
  
     Une info-bulle est affichée pour indiquer la population de ce cluster.  
  
5.  Maintenant, cliquez sur le **Variable d’ombrage** liste déroulante liste et choisissez le **âge** variable. Comme vous le faites, une liste de valeurs s’affiche dans le **état** zone de texte.  
  
     La colonne d'âge utilisée comme entrée de ce modèle contient des valeurs numériques continues, mais pour les besoins du clustering, l'algorithme discrétise toujours les nombres. Ici, vous pouvez voir les emplacements, ou les groupes créés par l’algorithme, tels que « très faible (\<= 27) » et « très élevée (> = 63) ».  
  
6.  À partir de la **état** listes déroulantes, sélectionnez **très élevée** et voir comment le diagramme change.  
  
     En modifiant la variable d'ombrage, vous pouvez voir d'un coup d'œil les clusters qui contiennent une plus grande part de cette catégorie d'âge cible, ainsi que les clusters qui contiennent très peu de clients dans cette catégorie d'âge.  
  
     ![Modifier le diagramme de cluster pour afficher l’âge](media/dm13-cluster-diagramshadebyage.gif "modifier le diagramme de cluster pour afficher l’âge")  
  
     Plus l'ombrage est foncé, plus la proportion de l'attribut cible et la distribution de valeurs sont importantes pour ce cluster.  
  
7.  Localisez le cluster dont l’ombrage est plus foncé lorsque le **Variable d’ombrage** est définie sur Age > 65.  
  
     Pointez le curseur de la souris sur le cluster.  
  
     La valeur affichée dans l'info-bulle indique maintenant la population de clients de ce cluster qui ont plus de 65 ans.  
  
8.  Cliquez sur le cluster et sélectionnez **renommer le Cluster**. Tapez un nouveau nom descriptif, comme **plus de 65 ans**. Le nouveau nom est enregistré avec le modèle sur le serveur et peut être utilisé pour identifier le cluster dans les autres vues de clustering.  
  
 [Retour au début](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterProfiles"></a> Profils du cluster  
 Le **profils du Cluster** onglet vous permet de comparer la composition de tous les clusters en un clin de œil. C'est le point de départ idéal pour vous familiariser avec le modèle. Cette vue sera également utile ultérieurement, si vous avez exploré un cluster particulier et que vous devez déterminer ceux qui y sont associés.  
  
 **Profils du cluster** vous donne également une bonne vue d’ensemble de la façon dont les clusters sont différents entre eux. Par conséquent, vous apprécierez peut-être le côté pratique de cette vue pour donner à chaque cluster un nom descriptif.  
  
##### <a name="explore-the-cluster-profiles"></a>Explorer les profils de cluster  
  
1.  Cliquez sur la cellule occupations (professions), dans le **états** colonne, pour afficher la liste de toutes les valeurs pour la profession.  
  
2.  Déplacez maintenant le curseur sur la profession dans les profils de cluster.  
  
     L'info-bulle affiche la distribution des professions dans ce cluster.  
  
     ![Afficher les valeurs détaillées dans les info-bulles ou la légende](media/dm13-cluster-profile-age-tooltip.gif "afficher les valeurs détaillées dans les info-bulles ou la légende")  
  
     Notez que, dans certains clusters (tel que celui dans le graphique), la liste de professions n’est pas terminée, et certaines professions sont remplacées par l’étiquette, **autres**.  
  
     Cela est inhérent à la conception ; en effet, il peut être difficile de faire la différence entre plusieurs barres de petite taille dans un histogramme. Par défaut uniquement les barres de plus grande importance sont conservées et les barres restantes sont regroupées dans un gris **autres** compartiment.  
  
     Pour modifier le nombre de barres qui sont visibles dans un histogramme, utilisez l’option **barres de l’histogramme**.  
  
3.  Notez que le **âge** colonne semble différente des autres. Cliquez sur le losange dans le graphique utilisé pour représenter l'âge.  
  
     La colonne Age (Âge) contenait à l'origine uniquement des nombres continus. L'algorithme de clustering requiert des valeurs discrètes ; il a donc regroupé les valeurs numériques de la colonne d'âge dans un nombre limité de tranches d'âges, en fonction de la distribution de valeurs.  
  
4.  Cliquez sur l'un des graphiques en losange dans un profil de cluster.  
  
     Ces graphiques en losange sont affichés uniquement lorsque les données sources utilisent des valeurs numériques continues. Les graphiques en losange fournissent des statistiques descriptives utiles, y compris la moyenne et l'écart type pour cette valeur dans chaque cluster :  
  
    -   La ligne dans le graphique en losange représente la plage de valeurs pour l'attribut. Les valeurs sont également affichées dans le **états** colonne à gauche de la **profils** graphique.  
  
    -   Le centre du losange est positionné à la moyenne du nœud.  
  
    -   La largeur du losange représente la variance de l'attribut à ce nœud. Par conséquent, un losange plus étroit indique que le nœud peut créer une prédiction plus précise.  
  
5.  Pour libérer de la place dans le graphique, cliquez sur un cluster, vous n’avez pas besoin afficher immédiatement, puis sélectionnez **masquer la colonne**. Cette opération ne le supprime pas du modèle, mais réduit juste la colonne temporairement.  
  
     Pour afficher les clusters que vous avez masqués, cliquez et faites glisser le bord de la colonne ou sélectionnez le nom du cluster dans la liste, **plus de clusters**.  
  
6.  Faites défiler la liste des attributs vers le bas jusqu'à ce que vous trouviez Bike Buyer, puis recherchez le cluster présentant le pourcentage le plus élevé de valeurs Oui.  
  
     Cliquez sur l’en-tête de colonne pour le cluster que vous souhaitez renommer, sélectionnez **renommer le cluster**et le type **acheteurs de vélo**.  
  
     Le nouveau nom de cluster est persistant dans toutes les vues, et sur le serveur, jusqu'à ce que vous traitiez une nouvelle fois le modèle.  
  
     ![Renommer les clusters pour faciliter l’utilisation de graphique](media/dm13-cluster-rename.gif "renommer les clusters pour faciliter l’utilisation de graphique")  
  
 **Conseils**  
  
-   Cliquez sur un en-tête de colonne pour trier les attributs par ordre d'importance pour ce cluster.  
  
-   Faites glisser les colonnes pour les réorganiser dans la visionneuse.  
  
-   Cliquez sur n’importe quelle cellule dans le graphique de profils pour afficher des statistiques détaillées dans le **légende d’exploration de données**.  
  
-   Avec le bouton droit n’importe quelle cellule et sélectionnez **colonnes du modèle d’extraction** pour générer les données sous-jacentes dans une nouvelle feuille de calcul Excel.  
  
-   Avec le bouton droit de titre et sélectionnez des colonnes du cluster **extraction pour structurer les données** pour obtenir des informations détaillées sur les membres du cluster qui n’a pas été incluses dans le modèle.  
  
     Par exemple, si vous définissez le profil de clients, vous pouvez laisser les coordonnées dans les données sous-jacentes (la structure d'exploration de données), mais ne pas les inclure dans le modèle, car elles ne sont pas utiles pour l'analyse. Cependant, une fois que les clients ont été attribués à des clusters, vous pouvez afficher les informations détaillées à l'aide de l'extraction.  
  
 [Retour au début](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterCharacteristics"></a> Caractéristiques du cluster  
 La vue Caractéristiques du cluster vous permet de vraiment explorer un cluster unique, afin de rechercher les attributs qui caractérisent le plus fortement ce groupe de données.  
  
##### <a name="explore-the-cluster-characteristics"></a>Explorer les caractéristiques du cluster  
  
1.  Sélectionnez le **plus de 65 ans** de cluster à partir de la **Cluster** liste.  
  
     Après avoir sélectionné un cluster, vous pouvez examiner en détail les caractéristiques qui composent ce cluster spécifique.  
  
     Les attributs contenus dans le cluster sont répertoriés dans les colonnes **Variables** et l'état de l'attribut répertorié est répertorié dans la colonne **Valeurs** .  
  
     États d’attribut sont répertoriés par ordre d’importance, avec leur probabilité dans ce cluster, représentée sous la forme d’une barre de couleur dans le **probabilité** colonne.  
  
     ![Caractéristiques d’un modèle de clustering](media/dm13-cluster-characteristics.gif "caractéristiques d’un modèle de clustering")  
  
2.  Cliquez sur le **Variables** colonne pour trier par attribut.  
  
     En modifiant la variable de tri, vous pouvez voir plus facilement comment les valeurs des variables telles que le revenu ou le fait d'être propriétaire d'une voiture, sont distribuées dans le groupe.  
  
3.  Cliquez sur **copier dans Excel**.  
  
     Une nouvelle feuille de calcul est ajoutée à votre classeur ; elle contient les caractéristiques du cluster sélectionné.  
  
4.  Choisissez maintenant un cluster différent dans la liste, **acheteurs de vélo**.  
  
5.  Cliquez sur **copier dans Excel**.  
  
     Notez que le nouveau graphique des caractéristiques du cluster est ajouté sur sa propre feuille de calcul. Vous pouvez le déplacer sur la même feuille de calcul que l'autre le profil pour faciliter la comparaison, ce que vous allez faire dans l'étape suivante.  
  
 **Conseils**  
  
-   Notez que la caractéristique principale du client dans le cluster des plus de 65 ans est que ces derniers n'achètent pas votre produit ! Si vous souhaitez en connaître la raison, vous pouvez parcourir les clusters et comparer les groupes, ou vous pouvez créer un modèle associé à l'aide d'un algorithme qui se prête à l'exploration des causes et des résultats, par exemple un modèle d'arbre de décision ou un modèle Naïve Bayes.  
  
-   Si vous voulez obtenir la liste complète des attributs et des probabilités pour ce cluster (ou l'ensemble des clusters), vous pouvez créer une requête. Pour obtenir des exemples de requêtes sur des modèles de clustering, consultez [exemples de requêtes modèle de Clustering](data-mining/clustering-model-query-examples.md).  
  
 [Retour au début](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterDiscrimination"></a> Discrimination de cluster  
 Vous utilisez le **Discrimination de Cluster** onglet pour comparer les attributs entre deux clusters, ou entre un cluster et tous les autres cas dans le jeu de données.  
  
 Pour mettre en évidence les fonctionnalités de cette visionneuse, nous allons les comparer aux tables côte à côte dans Excel que vous avez créé en fonction de la **caractéristiques du Cluster** vue.  
  
##### <a name="explore-cluster-discrimination"></a>Explorer la discrimination de cluster  
  
1.  Utilisez les listes **Cluster 1** et **Cluster 2** pour sélectionner les clusters à comparer.  
  
    -   Pour Cluster 1, sélectionnez les plus de 65 ans.  
  
    -   Pour Cluster 2, sélectionnez Bike Buyers.  
  
     La comparaison doit ressembler au graphique suivant.  
  
     ![comparaison de clusters dans un modèle](media/dm13-cluster-compareclusters.gif "comparaison de clusters dans un modèle")  
  
     Notez que, en coulisses, le **Discrimination de Cluster** visionneuse envoie des requêtes complexes pour le serveur d’exploration de données, pour extraire les attributs les plus importants pour établir une distinction entre les deux groupes, ce qui facilite la comparaison deux ensembles de clients.  
  
2.  Cliquez sur un de le **privilégie...** colonnes.  
  
     La barre à la droite de l'attribut et de la liste des valeurs montre les fonctionnalités ou les valeurs qui sont les plus importantes en tant que caractéristique du cluster sélectionné.  
  
3.  Comparez maintenant les listes dans Excel.  
  
     ![Réseau de dépendances pour un modèle d’association](media/dm13-comparing-profiles-in-excel.gif "réseau de dépendances pour un modèle d’association")  
  
     Comme les statistiques sous-jacentes qui étaient utilisées pour créer l'image dans la visionneuse sont enregistrées dans Excel sous forme de tableaux, vous pouvez filtrer et trier, ou encore afficher les valeurs réelles de probabilité.  
  
     En plus d'utiliser Excel, nous vous recommandons d'essayer la visionneuse de cluster pour Visio, qui vous permet également non seulement d'afficher des points de données, mais aussi de modifier en profondeur et d'améliorer le graphique. Pour plus d’informations, consultez [procédure pas à pas diagramme de Cluster &#40;Data Mining Add-ins&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md).  
  
 **Conseils**  
  
 Après avoir obtenu des informations sur les groupes de clients, essayez d’utiliser le [scénarios scénario &#40;Table Analysis Tools pour Excel&#41; ](what-if-scenario-table-analysis-tools-for-excel.md) ou [scénario de recherche d’objectif &#40;Table Analysis Tools pour Excel&#41; ](goal-seek-scenario-table-analysis-tools-for-excel.md) outils, pour Explorer les facteurs dans le modèle qui peut être modifié pour affecter le résultat.  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration des modèles dans Excel &#40;compléments d’exploration de données SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)   
 [Assistant cluster &#40;les données des compléments d’exploration de données pour Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
  
