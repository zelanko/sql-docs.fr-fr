---
title: Procédure pas à pas de diagramme (compléments d’exploration de données) de cluster | Microsoft Docs
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
- Visio shapes, cluster
- diagram, cluster
- shapes, data mining
- shapes, cluster
- data mining layout toolbar
ms.assetid: 761bef6a-37d4-4b19-944e-f2aadc75a242
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 808accf81389f97d2dff9383fe4c3fbe9d86068d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177256"
---
# <a name="cluster-diagram-walkthrough-data-mining-add-ins"></a>Procédure pas à pas Diagramme de cluster (Compléments d'exploration de données)
  Une fois que vous avez créé un modèle de clustering, vous pouvez l’importer dans Visio à l’aide du **Cluster** mettre en forme, puis continuer de personnaliser et d’améliorer la disposition. Le **formes d’exploration de données pour Visio** incluent les contrôles personnalisés suivants pour l’utilisation des diagrammes d’exploration de données :  
  
-   Contrôles de rendu du diagramme de cluster  
  
     Ces options font partie de la **Assistant Cluster** qui est exécuté lorsque vous déposez une forme dans l’espace de travail Visio.  
  
-   **Data Mining Layout** barre d’outils  
  
     Ces options sont ajoutées à l'espace de travail Visio pour vous aider à interagir avec la forme d'exploration de données. Ces options diffèrent selon le type de modèle d'exploration de données que vous utilisez.  
  
## <a name="build-a-cluster-diagram"></a>Créer un diagramme de cluster  
 Cette procédure pas à pas montre comment créer et personnaliser un diagramme de clustering dans Visio.  
  
 Pour pouvoir la suivre, vous devez disposer d'un modèle de clustering. Si vous n’avez pas d’un modèle, utilisez le [Assistant Cluster &#40;des compléments d’exploration de données pour Excel&#41; ](cluster-wizard-data-mining-add-ins-for-excel.md) Assistant et créer un modèle en utilisant le jeu de données d’apprentissage dans l’exemple de classeur, à l’aide de toutes les valeurs par défaut.  
  
#### <a name="use-the-cluster-visio-shape-wizard"></a>Utiliser l'Assistant Création de forme Cluster Visio  
  
1.  Si vous ne voyez pas **formes d’exploration de données Microsoft** dans le **formes** , cliquez sur **formes plus**, sélectionnez **ouvrir un gabarit**, puis ouvrez le modèle à partir de l’emplacement d’installation par défaut.  
  
     \<lecteur > : \Program files\Microsoft SQL Server 2012 DM Add-Ins  
  
2.  Faites glisser le **Cluster** forme sur la page.  
  
3.  Sur la page d’accueil de la **Assistant Création de forme Cluster Visio**, cliquez sur **suivant**.  
  
4.  Sur le **sélectionner une Source de données** page de la **Assistant Cluster**, choisir une connexion à un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] serveur qui contient les modèles d’exploration de données que vous souhaitez visualiser.  
  
5.  Sélectionnez un modèle d’exploration de données approprié, puis cliquez sur **suivant**.  
  
     Pour vous assurer que vous choisissez un modèle de clustering, passez en revue la description dans la **propriétés** volet.  
  
6.  Si la connexion est établie, dans la page, **Options du diagramme de cluster de**, décidez du type de diagramme de cluster à inclure dans votre présentation Visio :  
  
     **Afficher uniquement les formes de cluster**  
     Cette option crée un diagramme de cluster simple, chaque cluster étant représenté par un rectangle ou une autre forme que vous choisissez  
  
     **Afficher les clusters avec le graphique des caractéristiques**  
     Cette option crée le même graphique que précédemment, mais des histogrammes se trouvent à l'intérieur des formes pour décrire les caractéristiques du cluster.  
  
     ![Exemple de graphique des caractéristiques du cluster dans Visio](media/dm13-visio-cluster-samplecharshape.gif "exemple de graphique des caractéristiques du cluster dans Visio")  
  
     **Afficher les clusters avec le graphique de discrimination**  
     Cette option permet de créer le même graphique que le diagramme de cluster, mais elle répertorie les caractéristiques du cluster actuel qui le distinguent le plus fortement d'autres clusters.  
  
     Vous pouvez passer à un autre type de graphique une fois que l'Assistant a créé le diagramme. Pour cela, cliquez avec le bouton droit sur un cluster et sélectionnez un nouveau type de graphique. Pour l’instant, choisissez l’option, **afficher les clusters avec le graphique des caractéristiques**.  
  
7.  Laissez l’option **nombre de lignes dans le graphique**, en tant que 5.  
  
     Cette option ne modifie pas le nombre de clusters dans le modèle ; elle limite simplement le nombre d'attributs pouvant être affichés comme fonctionnalités de chaque cluster.  
  
     Cependant, l'option joue le rôle de filtre sur les données du graphique ; vous ne pouvez donc pas augmenter le nombre d'éléments ultérieurement.  
  
8.  Cliquez sur **Avancé**.  
  
     Le **Options de Cluster** boîte de dialogue est que vous personnalisez l’apparence visuelle des formes utilisées dans le diagramme. Vous pouvez modifier les couleurs utilisées dans le graphique et la forme utilisée pour les clusters.  
  
     Le **Variable d’ombrage** contrôle ne fonctionne pas dans Office 2013.  
  
     ![Cliquez sur Avancé pour choisir les couleurs des formes](media/dm13-visio-clusteroptions-advanced.gif "cliquez sur Avancé pour choisir les couleurs des formes")  
  
     **Conseil :** certaines couleurs peuvent être modifiées ultérieurement à l’aide de thèmes Visio et des contrôles d’édition de forme. Toutefois, les thèmes Visio remplaceront également certaines de ces sélections de couleurs ; par conséquent, nous recommandons de commencer par les couleurs par défaut et d'appliquer les modifications progressivement.  
  
9. Cliquez sur **Terminer** pour créer le graphique.  
  
     L'Assistant récupère les informations du modèle d'exploration de données, génère un rendu des formes et remplit chaque cluster avec des attributs et des valeurs.  
  
     ![un réseau de dépendances](media/dm13-visiodepnet-defaultgraph.gif "un réseau de dépendances")  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Explorer et modifier le diagramme terminé  
 Une fois le diagramme terminé, vous pouvez continuer à personnaliser son apparence avec les contrôles Visio, comme illustré dans l'exemple suivant.  
  
 ![diagramme de cluster personnalisé à l’aide de Visio](media/dm13-visio-clustercomplete1.gif "diagramme de cluster personnalisé à l’aide de Visio")  
  
 Toutes les formes de cluster de base sont générées par l'Assistant ; utilisez les outils suivants pour mettre à jour et personnaliser le diagramme :  
  
1.  Faites glisser le curseur le **Options de Cluster** contrôle, pour filtrer les relations les plus faibles et simplifier le diagramme.  
  
2.  Utilisez Visio **Redisposition** option pour faire des essais avec les dispositions de cluster différentes.  
  
3.  Utilisez le **connecteurs** option sur le **conception** onglet pour modifier le style de connecteur pour empêcher les lignes de croiser les clusters.  
  
4.  Cliquez sur le **Add-Ins** ruban et afficher une barre d’outils personnalisées utilisées pour travailler avec des diagrammes d’exploration de données :  
  
     **Mise en page**  
     Optimise la disposition des clusters pour qu'ils tiennent sur la page active.  
  
     **Redimensionner la Page**  
     Ce contrôle a été conçu pour les versions HTML antérieures. Utilisez plutôt les contrôles de redimensionnement de page Visio.  
  
     **Description**  
     Si un cluster est sélectionné, cliquez sur cette option pour afficher des détails sur le cluster.  
  
     ![Cliquez sur Description pour obtenir des détails sur le cluster](media/dm13-visio-cluster-description-control.gif "cliquez sur Description pour obtenir des détails sur le cluster")  
  
     **Résistance du bord**  
     Affiche les scores de confiance sur les lignes reliant les clusters.  
  
     Cependant, si vous appliquez une mise en forme spéciale autre que la valeur par défaut générée par l'Assistant, y compris certains arrière-plans, ces valeurs peuvent ne pas être visibles.  
  
     **Curseur**  
     Filtre les lignes entre les clusters. Le fait de déplacer le curseur vers le haut supprime toutes les associations, sauf les plus importantes.  
  
     **Ombrage**  
     Ce contrôle ne fonctionne pas dans Office 2013.  
  
5.  Utilisez le **panoramique et Zoom** contrôle, dans le **volet** zone de Visio **vue** ruban pour vous concentrer sur un ensemble de clusters et vous déplacer dans le diagramme.  
  
6.  Cliquez avec le bouton droit sur un cluster pour afficher les options spécifiques à la forme du cluster :  
  
    -   Modifiez le style du graphique.  
  
    -   Ajoutez un graphique des caractéristiques du cluster.  
  
    -   Ajoutez un graphique de discrimination de cluster.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des diagrammes d’exploration de données Visio &#40;compléments d’exploration de données SQL Server&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
