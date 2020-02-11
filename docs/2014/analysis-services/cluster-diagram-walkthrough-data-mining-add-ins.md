---
title: Procédure pas à pas sur le diagramme de cluster (compléments d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Visio shapes, cluster
- diagram, cluster
- shapes, data mining
- shapes, cluster
- data mining layout toolbar
ms.assetid: 761bef6a-37d4-4b19-944e-f2aadc75a242
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fc2df250b0728934f258c8217d29adfb91e66ff5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087913"
---
# <a name="cluster-diagram-walkthrough-data-mining-add-ins"></a>Procédure pas à pas Diagramme de cluster (Compléments d'exploration de données)
  Une fois que vous avez créé un modèle de clustering, vous pouvez l’importer dans Visio à l’aide de la forme **cluster** , puis continuer à personnaliser et améliorer la disposition. Les **formes d’exploration de données pour Visio** incluent les contrôles personnalisés suivants pour l’utilisation des diagrammes d’exploration de données :  
  
-   Contrôles de rendu du diagramme de cluster  
  
     Ces options font partie de l' **Assistant cluster** qui est lancé lorsque vous déposez une forme dans l’espace de travail Visio.  
  
-   Barre d’outils de **disposition d’exploration de données**  
  
     Ces options sont ajoutées à l'espace de travail Visio pour vous aider à interagir avec la forme d'exploration de données. Ces options diffèrent selon le type de modèle d'exploration de données que vous utilisez.  
  
## <a name="build-a-cluster-diagram"></a>Créer un diagramme de cluster  
 Cette procédure pas à pas montre comment créer et personnaliser un diagramme de clustering dans Visio.  
  
 Pour pouvoir la suivre, vous devez disposer d'un modèle de clustering. Si vous n’avez pas de modèle, utilisez l' [Assistant Cluster &#40;les compléments d’exploration de données pour Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) Assistant et créez un modèle à l’aide du jeu de données d’apprentissage dans l’exemple de classeur, en utilisant toutes les valeurs par défaut.  
  
#### <a name="use-the-cluster-visio-shape-wizard"></a>Utiliser l'Assistant Création de forme Cluster Visio  
  
1.  Si les **formes d’exploration de données Microsoft** ne s’affichent pas dans la liste **formes** , cliquez sur **autres formes**, sélectionnez **ouvrir le stencil**, puis ouvrez le modèle à partir de l’emplacement d’installation par défaut.  
  
     \<lecteur> : \Program files\Microsoft SQL Server 2012 DM Add-ins  
  
2.  Faites glisser la forme **cluster** sur la page.  
  
3.  Sur la page d’accueil de l' **Assistant Création de forme cluster Visio**, cliquez sur **suivant**.  
  
4.  Dans la page **Sélectionner une source de données** de l' **Assistant cluster**, choisissez une connexion à [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] un serveur qui contient les modèles d’exploration de données que vous souhaitez visualiser.  
  
5.  Sélectionnez un modèle d’exploration de données approprié, puis cliquez sur **suivant**.  
  
     Pour vous assurer que vous choisissez un modèle de clustering, passez en revue la description dans le volet **Propriétés** .  
  
6.  Si la connexion réussit, sur la page **Options du diagramme de cluster**, vous décidez du type de diagramme de cluster à inclure dans votre présentation Visio :  
  
     **Afficher uniquement les formes de cluster**  
     Cette option crée un diagramme de cluster simple, chaque cluster étant représenté par un rectangle ou une autre forme que vous choisissez  
  
     **Afficher les clusters avec le graphique des caractéristiques**  
     Cette option crée le même graphique que précédemment, mais des histogrammes se trouvent à l'intérieur des formes pour décrire les caractéristiques du cluster.  
  
     ![Exemple de graphique des caractéristiques de cluster dans Visio](media/dm13-visio-cluster-samplecharshape.gif "Exemple de graphique des caractéristiques de cluster dans Visio")  
  
     **Afficher les clusters avec le graphique de discrimination**  
     Cette option permet de créer le même graphique que le diagramme de cluster, mais elle répertorie les caractéristiques du cluster actuel qui le distinguent le plus fortement d'autres clusters.  
  
     Vous pouvez passer à un autre type de graphique une fois que l'Assistant a créé le diagramme. Pour cela, cliquez avec le bouton droit sur un cluster et sélectionnez un nouveau type de graphique. Pour le moment, choisissez l’option **afficher les clusters avec le graphique des caractéristiques**.  
  
7.  Laissez l’option, **nombre de lignes dans le graphique**, en tant que 5.  
  
     Cette option ne change pas le nombre de clusters dans le modèle ; Il limite simplement le nombre d’attributs pouvant être affichés en tant que fonctionnalités de chaque cluster.  
  
     Toutefois, l’option agit comme un filtre sur les données du graphique. vous ne pouvez donc pas augmenter le nombre d’éléments ultérieurement.  
  
8.  Cliquez sur **Avancé**.  
  
     La boîte de dialogue **options de cluster** vous permet de personnaliser l’apparence visuelle des formes utilisées dans le diagramme. Vous pouvez modifier les couleurs utilisées dans le graphique et la forme utilisée pour les clusters.  
  
     Le contrôle de **variable d’ombrage** ne fonctionne pas dans Office 2013.  
  
     ![cliquez Avancées pour choisir les couleurs des formes](media/dm13-visio-clusteroptions-advanced.gif "cliquez Avancées pour choisir les couleurs des formes")  
  
     **Conseil :** Certaines couleurs peuvent être modifiées ultérieurement à l’aide des thèmes Visio et des contrôles d’édition de forme. Toutefois, les thèmes Visio remplaceront également certaines de ces sélections de couleurs ; par conséquent, nous recommandons de commencer par les couleurs par défaut et d'appliquer les modifications progressivement.  
  
9. Cliquez sur **Terminer** pour créer le graphique.  
  
     L'Assistant récupère les informations du modèle d'exploration de données, génère un rendu des formes et remplit chaque cluster avec des attributs et des valeurs.  
  
     ![un réseau de dépendances](media/dm13-visiodepnet-defaultgraph.gif "un réseau de dépendances")  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Explorer et modifier le diagramme terminé  
 Une fois le diagramme terminé, vous pouvez continuer à personnaliser son apparence avec les contrôles Visio, comme illustré dans l'exemple suivant.  
  
 ![diagramme de cluster personnalisé avec Visio](media/dm13-visio-clustercomplete1.gif "diagramme de cluster personnalisé avec Visio")  
  
 Toutes les formes de cluster de base sont générées par l'Assistant ; utilisez les outils suivants pour mettre à jour et personnaliser le diagramme :  
  
1.  Faites glisser le curseur dans le contrôle **options de cluster** pour filtrer les relations plus faibles et simplifier le diagramme.  
  
2.  Utilisez l’option de **page nouvelle disposition** de Visio pour expérimenter différentes dispositions de cluster.  
  
3.  Utilisez l’option **connecteurs** sous l’onglet **conception** pour modifier le style de connecteur afin que les lignes ne traversent pas les clusters.  
  
4.  Cliquez sur le ruban **compléments** , puis affichez l’une des barres d’outils personnalisées utilisées pour travailler avec les diagrammes d’exploration de données :  
  
     **Disposition**  
     Optimise la disposition des clusters pour qu'ils tiennent sur la page active.  
  
     **Redimensionner la page**  
     Ce contrôle a été conçu pour les versions HTML antérieures. Utilisez plutôt les contrôles de redimensionnement de page Visio.  
  
     **Description**  
     Si un cluster est sélectionné, cliquez sur cette option pour afficher des détails sur le cluster.  
  
     ![cliquez sur Description pour obtenir des informations sur le cluster](media/dm13-visio-cluster-description-control.gif "cliquez sur Description pour obtenir des informations sur le cluster")  
  
     **Résistance du bord**  
     Affiche les scores de confiance sur les lignes reliant les clusters.  
  
     Cependant, si vous appliquez une mise en forme spéciale autre que la valeur par défaut générée par l'Assistant, y compris certains arrière-plans, ces valeurs peuvent ne pas être visibles.  
  
     **Curseur**  
     Filtre les lignes entre les clusters. Le fait de déplacer le curseur vers le haut supprime toutes les associations, sauf les plus importantes.  
  
     **Ombrage**  
     Ce contrôle ne fonctionne pas dans Office 2013.  
  
5.  Utilisez le contrôle **panoramique et zoom** , dans la zone **volet de tâches** du ruban **affichage** Visio, pour vous concentrer sur un ensemble de clusters et vous déplacer dans le diagramme.  
  
6.  Cliquez avec le bouton droit sur un cluster pour afficher les options spécifiques à la forme du cluster :  
  
    -   Modifiez le style du graphique.  
  
    -   Ajoutez un graphique des caractéristiques du cluster.  
  
    -   Ajoutez un graphique de discrimination de cluster.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des diagrammes d’exploration de données Visio &#40;SQL Server des compléments d’exploration de données&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
