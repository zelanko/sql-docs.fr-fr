---
title: Exploration du modèle de clustering (didacticiel sur l’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce8aa034-161b-473f-baec-9c29e0a8e5f5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9bb2c6457122a5ea49824ca178b6950d88f75563
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63280433"
---
# <a name="exploring-the-clustering-model-basic-data-mining-tutorial"></a>Exploration du modèle de clustering (Didacticiel sur l'exploration de données de base)
  L' [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme de clustering regroupe les cas en clusters qui contiennent des caractéristiques similaires. Ces regroupements sont utiles pour l'exploration des données, l'identification d'anomalies dans les données et la création de prédictions.  
  
 
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Cluster Viewer fournit les onglets suivants pour explorer les modèles d'exploration de données de clustering :  
  

  
##  <a name="ClusterDiagramTab"></a>Onglet diagramme de cluster  
 L'onglet Diagramme de cluster affiche tous les clusters qui sont dans un modèle d'exploration de données. Les lignes entre les clusters représentent le lien logique et sont plus ou moins ombrées selon le degré de similitude entre les clusters. La couleur actuelle de chaque cluster représente la fréquence de la variable et l'état dans le cluster.  
  
#### <a name="to-explore-the-model-in-the-cluster-diagram-tab"></a>Pour explorer le modèle dans l'onglet Diagramme de cluster  
  
1.  Utilisez la liste **modèle d’exploration de données** en haut de l’onglet **visionneuse de modèle** d' `TM_Clustering` exploration de données pour basculer vers le modèle.  
  
2.  Dans la liste **visionneuse** , sélectionnez **Microsoft Cluster Viewer**.  
  
3.  Dans la zone **variable d’ombrage** , sélectionnez **vélos Buyer**.  
  
     La variable par défaut est **remplissage**, mais vous pouvez la remplacer par n’importe quel attribut du modèle, afin de découvrir les clusters qui contiennent des membres ayant les attributs souhaités.  
  
4.  Sélectionnez **1** dans la zone **État** pour explorer les cas où un vélo a été acheté.  
  
     La légende **densité** décrit la densité de la paire état d’attribut sélectionnée dans la variable d’ombrage et l’État. Dans cet exemple, il nous dit que le clusterwith l’ombrage le plus foncé a le pourcentage le plus élevé d’acheteurs de vélos.  
  
5.  Arrêtez votre souris sur le cluster avec l'ombrage le plus foncé.  
  
     Une info-bulle affiche le pourcentage des cas qui ont l'attribut, `Bike Buyer = 1`.  
  
6.  Sélectionnez le cluster ayant la densité la plus élevée, cliquez avec le bouton droit sur le cluster, sélectionnez **Renommer le cluster** et tapez Bike Buyers **High** pour une identification ultérieure. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Recherchez le cluster qui a l'ombrage le plus clair (et la densité la plus faible). Cliquez avec le bouton droit sur le cluster, sélectionnez **Renommer le cluster** et tapez Bike Buyers **Low**. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  Cliquez sur le cluster Bike Buyers **High** et faites-le glisser vers une zone du volet qui vous donnera un aperçu clair de ses connexions aux autres clusters.  
  
     Lorsque vous sélectionnez un cluster, les lignes qui connectent ce cluster aux autres clusters sont mises en surbrillance, afin que vous puissiez consulter facilement toutes les relations du cluster. Lorsque le cluster n'est pas sélectionné, vous pouvez connaître d'après l'obscurité des lignes le degré de force des relations entre tous les clusters du diagramme. Si l'ombrage est clair ou inexistant, les clusters ne sont pas très similaires.  
  
9. En utilisant le curseur à gauche du réseau, vous pouvez appliquer un filtre pour exclure les liens les moins forts et rechercher les clusters liés par une relation étroite. Le service marketing [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] peut vouloir associer les clusters similaires pour déterminer la meilleure méthode pour remettre le publipostage ciblé.  
  

  
##  <a name="ClusterProfilesTab"></a>Onglet Profils du cluster  
 L’onglet **profils du cluster** fournit une vue d’ensemble `TM_Clustering` du modèle. L’onglet **profils du cluster** contient une colonne pour chaque cluster du modèle. La première colonne contient la liste des attributs associés à au moins un cluster. Les autres colonnes de la visionneuse contiennent la distribution des états d'un attribut pour chaque cluster. La distribution d’une variable discrète est indiquée sous la forme d’une barre de couleur avec le nombre maximal de barres affichées dans la liste barres de l' **histogramme** . Les attributs continus sont affichés avec un graphique en losange qui représente l'écart moyen et l'écart type dans chaque cluster.  
  
#### <a name="to-explore-the-model-in-the-cluster-profiles-tab"></a>Pour explorer le modèle dans l'onglet Profils du cluster  
  
1.  Définissez barres de l' **histogramme** sur **5**.  
  
     Dans notre modèle, 5 est le nombre maximal d'états pour toute variable.  
  
2.  Si la **légende d’exploration de données** bloque l’affichage des **profils d’attribut**, déplacez-le hors de la voie.  
  
3.  Sélectionnez la colonne Bike Buyers **High** et faites-la glisser vers la droite de la colonne **population** .  
  
4.  Sélectionnez la colonne Bike Buyers **Low** et faites-la glisser vers la droite de la colonne Bike Buyers **High** .  
  
5.  Cliquez sur la colonne Bike Buyers **High** .  
  
     La colonne **variables** est triée par ordre d’importance pour ce cluster. Faites défiler la colonne et examinez les caractéristiques du cluster Bike Buyer High. Par exemple, elles sont plus susceptibles d'effectuer des trajets courts domicile-travail.  
  
6.  Double-cliquez sur la cellule **Age** dans la colonne Bike Buyers **High** .  
  
     La **légende d’exploration de données** affiche une vue plus détaillée et vous pouvez voir la tranche d’âge de ces clients, ainsi que l’âge moyen.  
  
7.  Cliquez avec le bouton droit sur la colonne Bike Buyers **Low** et sélectionnez **masquer la colonne**.  
  

  
##  <a name="ClusterCharacteristicsTab"></a>Onglet caractéristiques du cluster  
 Avec l’onglet **caractéristiques du cluster** , vous pouvez examiner plus en détail les caractéristiques qui composent un cluster. Au lieu de comparer les caractéristiques de tous les clusters (comme dans l'onglet Profils du cluster), vous pouvez explorer un cluster à la fois. Par exemple, si vous sélectionnez **Bike** Buyers High dans la liste **cluster** , vous pouvez voir les caractéristiques des clients dans ce cluster. Même si l'affichage est différent de la visionneuse Profils du cluster, les conclusions sont les mêmes.  
  
> [!NOTE]  
>  À moins que vous n’ayez défini une valeur initiale pour **HoldoutSeed**, les résultats varient chaque fois que vous traitez le modèle. Pour plus d’informations, consultez [élément HoldoutSeed](https://docs.microsoft.com/bi-reference/assl/properties/holdoutseed-element)  
  

  
##  <a name="ClusterDiscriminationTab"></a>Onglet discrimination de cluster  
 L’onglet **discrimination de cluster** vous permet d’explorer les caractéristiques qui distinguent un cluster d’un autre. Une fois que vous avez sélectionné deux clusters, l’un dans la liste **cluster 1** et l’autre dans la liste **cluster 2** , la visionneuse calcule les différences entre les clusters et affiche une liste des attributs qui distinguent la plupart des clusters.  
  
#### <a name="to-explore-the-model-in-the-cluster-discrimination-tab"></a>Pour explorer le modèle dans l'onglet Discrimination de cluster  
  
1.  Dans la zone **cluster 1** , sélectionnez **Bike**Buyers High.  
  
2.  Dans la zone **cluster 2** , sélectionnez **Bike**Buyers Low.  
  
3.  Cliquez sur **variables** pour trier par ordre alphabétique.  
  
     Parmi les différences les plus importantes entre les clients dans les clusters les plus **bas** et les **acheteurs de vélo** , citons l’âge, la propriété de la voiture, le nombre d’enfants et la région.  
  
## <a name="related-tasks"></a>Tâches associées  
 Voir les rubriques qui suivent pour explorer les autres modèles d'exploration de données.  
  
-   [Exploration du modèle d’arbre de décision &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Exploration du modèle Naive Bayes &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Exploration du modèle Naive Bayes &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Exploration du modèle d’arbre de décision &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Parcourir un modèle à l’aide de Microsoft Cluster Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)   
 [Onglet discrimination de cluster &#40;la visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md)   
 [Onglet Profils du cluster &#40;la visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md)   
 [Onglet caractéristiques du cluster &#40;la visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md)   
 [Onglet diagramme de cluster &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)  
  
  
