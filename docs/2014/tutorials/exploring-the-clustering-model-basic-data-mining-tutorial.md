---
title: Exploration du modèle de Clustering (didacticiel d’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: ce8aa034-161b-473f-baec-9c29e0a8e5f5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 26869ca780bc74e3c9c56b38b39195b893dbf523
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48147769"
---
# <a name="exploring-the-clustering-model-basic-data-mining-tutorial"></a>Exploration du modèle de clustering (Didacticiel sur l'exploration de données de base)
  Le [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme de Clustering regroupe des cas dans des clusters qui présentent des caractéristiques similaires. Ces regroupements sont utiles pour l'exploration des données, l'identification d'anomalies dans les données et la création de prédictions.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Cluster Viewer fournit les onglets suivants pour explorer les modèles d'exploration de données de clustering :  
  

  
##  <a name="ClusterDiagramTab"></a> Onglet Diagramme de cluster  
 L'onglet Diagramme de cluster affiche tous les clusters qui sont dans un modèle d'exploration de données. Les lignes entre les clusters représentent le lien logique et sont plus ou moins ombrées selon le degré de similitude entre les clusters. La couleur actuelle de chaque cluster représente la fréquence de la variable et l'état dans le cluster.  
  
#### <a name="to-explore-the-model-in-the-cluster-diagram-tab"></a>Pour explorer le modèle dans l'onglet Diagramme de cluster  
  
1.  Utilisez le **Mining Model** liste en haut de la **visionneuse de modèle d’exploration de données** tab pour passer à la `TM_Clustering` modèle.  
  
2.  Dans le **visionneuse** liste, sélectionnez **Microsoft Cluster Viewer**.  
  
3.  Dans le **Variable d’ombrage** boîte, sélectionnez **Bike Buyer**.  
  
     La variable par défaut est **Population**, mais vous pouvez le modifier à tout attribut dans le modèle, pour découvrir quels clusters contiennent des membres qui ont les attributs souhaités.  
  
4.  Sélectionnez **1** dans le **état** boîte pour Explorer les cas où un vélo a été acheté.  
  
     Le **densité** légende décrit la densité de la paire d’état d’attribut sélectionnée dans la Variable d’ombrage et de l’état. Dans cet exemple nous saurons ainsi que le clusterwith l’ombrage le plus foncé a le pourcentage le plus élevé d’acheteurs de vélo.  
  
5.  Arrêtez votre souris sur le cluster avec l'ombrage le plus foncé.  
  
     Une info-bulle affiche le pourcentage des cas qui ont l'attribut, `Bike Buyer = 1`.  
  
6.  Sélectionnez le cluster ayant la densité la plus élevée, cliquez sur le cluster, sélectionnez **renommer le Cluster** et type **Bike Buyers High** pour l’identification ultérieure. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Recherchez le cluster qui a l'ombrage le plus clair (et la densité la plus faible). Cliquez sur le cluster, sélectionnez **renommer le Cluster** et type **Bike Buyers Low**. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Cliquez sur le **Bike Buyers High** de cluster et faites-le glisser vers une zone du volet qui vous donnera un aperçu clair de ses connexions aux autres clusters.  
  
     Lorsque vous sélectionnez un cluster, les lignes qui connectent ce cluster aux autres clusters sont mises en surbrillance, afin que vous puissiez consulter facilement toutes les relations du cluster. Lorsque le cluster n'est pas sélectionné, vous pouvez connaître d'après l'obscurité des lignes le degré de force des relations entre tous les clusters du diagramme. Si l'ombrage est clair ou inexistant, les clusters ne sont pas très similaires.  
  
9. En utilisant le curseur à gauche du réseau, vous pouvez appliquer un filtre pour exclure les liens les moins forts et rechercher les clusters liés par une relation étroite. Le service marketing [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] peut vouloir associer les clusters similaires pour déterminer la meilleure méthode pour remettre le publipostage ciblé.  
  

  
##  <a name="ClusterProfilesTab"></a> Onglet Profils du cluster  
 Le **profils du Cluster** onglet fournit une vue d’ensemble de la `TM_Clustering` modèle. Le **profils du Cluster** onglet contient une colonne pour chaque cluster dans le modèle. La première colonne contient la liste des attributs associés à au moins un cluster. Les autres colonnes de la visionneuse contiennent la distribution des états d'un attribut pour chaque cluster. La distribution d’une variable discrète est affichée comme une barre de couleur avec le nombre maximal de barres affichées dans le **barres de l’histogramme** liste. Les attributs continus sont affichés avec un graphique en losange qui représente l'écart moyen et l'écart type dans chaque cluster.  
  
#### <a name="to-explore-the-model-in-the-cluster-profiles-tab"></a>Pour explorer le modèle dans l'onglet Profils du cluster  
  
1.  Définissez **histogramme** barres de **5**.  
  
     Dans notre modèle, 5 est le nombre maximal d'états pour toute variable.  
  
2.  Si le **légende d’exploration de données** bloque l’affichage de la **profils d’attribut**, déplacez-le disparaître.  
  
3.  Sélectionnez le **Bike Buyers High** colonne et faites-le glisser vers la droite de la **Population** colonne.  
  
4.  Sélectionnez le **Bike Buyers Low** colonne et faites-le glisser vers la droite de la **Bike Buyers High** colonne.  
  
5.  Cliquez sur le **Bike Buyers High** colonne.  
  
     Le **Variables** colonne est triée par ordre d’importance pour ce cluster. Faites défiler la colonne et examinez les caractéristiques du cluster Bike Buyer High. Par exemple, elles sont plus susceptibles d'effectuer des trajets courts domicile-travail.  
  
6.  Double-cliquez sur le **âge** de cellule dans le **Bike Buyers High** colonne.  
  
     Le **légende d’exploration de données** affiche plus détaillées vue et que vous pouvez voir les tranches d’âge de ces clients, ainsi que l’âge moyen.  
  
7.  Cliquez sur le **Bike Buyers Low** colonne, puis sélectionnez **masquer la colonne**.  
  

  
##  <a name="ClusterCharacteristicsTab"></a> Onglet caractéristiques du cluster  
 Avec le **caractéristiques du Cluster** onglet, vous pouvez examiner plus en détail les caractéristiques qui composent un cluster. Au lieu de comparer les caractéristiques de tous les clusters (comme dans l'onglet Profils du cluster), vous pouvez explorer un cluster à la fois. Par exemple, si vous sélectionnez **Bike Buyers High** à partir de la **Cluster** liste, vous pouvez consulter les caractéristiques des clients dans ce cluster. Même si l'affichage est différent de la visionneuse Profils du cluster, les conclusions sont les mêmes.  
  
> [!NOTE]  
>  Sauf si vous définissez une valeur initiale pour **holdoutseed**, les résultats varient chaque fois que vous traitez le modèle. Pour plus d’informations, consultez [holdoutseed, élément](../analysis-services/scripting/properties/holdoutseed-element.md)  
  

  
##  <a name="ClusterDiscriminationTab"></a> Onglet Discrimination de cluster  
 Avec le **Discrimination de Cluster** onglet, vous pouvez explorer les caractéristiques qui différencient un cluster à partir d’un autre. Une fois que vous sélectionnez deux clusters, une à partir de la **Cluster 1** liste et l’autre le **Cluster 2** liste, la visionneuse calcule les différences entre les clusters et affiche une liste des attributs qui différencient le plus.  
  
#### <a name="to-explore-the-model-in-the-cluster-discrimination-tab"></a>Pour explorer le modèle dans l'onglet Discrimination de cluster  
  
1.  Dans le **Cluster 1** boîte, sélectionnez **Bike Buyers High**.  
  
2.  Dans le **Cluster 2** boîte, sélectionnez **Bike Buyers Low**.  
  
3.  Cliquez sur **Variables** pour trier par ordre alphabétique.  
  
     Certaines des différences plus significatives parmi les clients dans le **Bike Buyers Low** et **Bike Buyers High** clusters incluent l’âge, la propriété de voiture, le nombre d’enfants et la région.  
  
## <a name="related-tasks"></a>Tâches associées  
 Voir les rubriques qui suivent pour explorer les autres modèles d'exploration de données.  
  
-   [Exploration du modèle Decision Tree &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Exploration du modèle Naive Bayes &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Exploration du modèle Naive Bayes &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Exploration du modèle Decision Tree &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Explorer un modèle à l’aide de Microsoft Cluster Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)   
 [Onglet Discrimination de cluster &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md)   
 [Onglet Profils de cluster &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md)   
 [Onglet caractéristiques du cluster &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md)   
 [Onglet Diagramme de cluster &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)  
  
  
