---
title: Procédure pas à pas sur le diagramme d’arbre de décision (compléments d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- shapes, data mining
- diagram, decision tree
- Visio shapes, decision tree
- decision tree [data mining]
ms.assetid: 9566f6a2-c750-4125-ba5e-42c7251a78c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 755a7f9c8708664dbb3a65c223873cf1dd4e20c8
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528865"
---
# <a name="decision-tree-diagram-walkthrough--data-mining-add-ins"></a>Procédure pas à pas sur le diagramme d’arbre de décision (compléments d’exploration de données)
  Si vous avez créé un modèle d'arbre de décision, vous pouvez créer un diagramme personnalisé dans Visio à l'aide de la forme Arbre de décision ou de la forme Réseau de dépendances. Cette rubrique décrit les personnalisations que vous pouvez effectuer à l’aide de la forme **arbre de décision** et de ces contrôles :  
  
-   Contrôles de rendu pour le diagramme d'arbre de décision  
  
     Ces options font partie de l **'Assistant arbre de décision** qui est lancé lorsque vous déposez une forme dans l’espace de travail Visio.  
  
-   Barre d’outils de **disposition d’exploration de données**  
  
     Ces options sont ajoutées à l'espace de travail Visio pour vous aider à interagir avec la forme.  
  
## <a name="build-a-decision-tree-diagram"></a>Créer un diagramme d'arbre de décision  
 Vous déposez la forme arbre de décision sur la page Visio pour lancer l' **Assistant Création de forme arbre de décision Visio** et définir les options du diagramme.  
  
#### <a name="use-the-decision-tree-wizard"></a>Utiliser l'Assistant Arbre de décision  
  
1.  Si les **formes d’exploration de données Microsoft** ne s’affichent pas dans la liste **formes** , cliquez sur **autres formes**, sélectionnez **ouvrir le stencil**, puis ouvrez le modèle à partir de l’emplacement d’installation par défaut.  
  
     \<drive>: \Program Files (x85) \Microsoft SQL Server 2012 DM Add-ins  
  
2.  Faites glisser la forme **arbre de décision** sur la page.  
  
3.  Sur la page d’accueil de l **'Assistant Création de forme arbre de décision Visio**, cliquez sur **suivant**.  
  
4.  Dans la page **Sélectionner une source de données** de l' **Assistant cluster**, choisissez une connexion à un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] serveur dont vous souhaitez visualiser le modèle.  
  
5.  Sélectionnez un modèle d’exploration de données approprié, puis cliquez sur **suivant**.  
  
     Ce type de diagramme prend en charge les modèles créés à l'aide de l'algorithme Decision Trees ou Linear Regression.  
  
6.  Dans la page **Sélectionner l’arbre de décision** , choisissez une arborescence individuelle à afficher.  
  
     Une arborescence modélise les interactions qui mènent à un résultat particulier que vous avez modélisé. par conséquent, même si votre modèle contient plusieurs résultats, vous ne pouvez afficher qu’une seule arborescence à la fois.  
  
7.  Dans la boîte de dialogue **Sélectionner un arbre de décision** , vous pouvez également définir ces options de rendu :  
  
     **Profondeur de rendu maximum**  
     Utilisez cette option pour contrôler le nombre de nœuds qui sont affichés.  
  
     Un arbre de décision peut être très profond, ce qui entraîne la création d'un diagramme qui ne tient pas sur la page. Utilisez ce contrôle pour vous concentrer sur les nœuds situés les plus à gauche, qui sont les plus importants.  
  
     La valeur par défaut est trois niveaux de nœuds.  
  
     **Sélectionner la couleur et le texte à afficher pour les valeurs**  
     Choisissez la couleur qui représentera chacun des résultats. Si vous ne spécifiez pas de couleurs, elles sont générées automatiquement avec les couleurs des thèmes vidéo actuels.  
  
8.  Cliquez sur **avancé** pour personnaliser les options suivantes pour chacun des nœuds du diagramme de l’arbre de décision.  
  
     **Variable d’ombrage** et **État**  
     Sélectionnez le résultat cible que vous souhaitez afficher dans le diagramme d'arborescence.  
  
     **Afficher l'histogramme**  
     Ajoute un graphique à chaque nœud qui affiche les règles qui définissent ce nœud.  
  
     **Afficher l'étiquette**  
     Ajoute des noms de colonne à l'histogramme.  
  
     **Afficher la probabilité**  
     Affiche la probabilité de chaque valeur.  
  
     **Afficher la prise en charge**  
     Affiche la prise en charge de chaque valeur.  
  
     **Afficher le pied**  
     Ajoute un pied de page qui additionne toutes les valeurs affichées.  
  
     **Afficher l'en-tête**  
     Affiche les en-têtes de colonne.  
  
     **Afficher les états sans aucune prise en charge**  
     Vous permet d'afficher les valeurs manquantes.  
  
9. Cliquez sur **Terminer** pour créer le graphique.  
  
    > [!WARNING]  
    >  Dans certains environnements, les connecteurs dans le graphique peuvent ne pas être rendus dans Office 2013.  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Explorer et modifier le diagramme terminé  
 Une fois que vous avez terminé l' **Assistant Création de forme arbre de décision Visio**, Visio crée un diagramme d’arborescence sur la page qui affiche graphiquement les règles qui mènent au résultat prédit.  
  
 Vous pouvez continuer à modifier la forme en utilisant les contrôles suivants pour les diagrammes d'arbre de décision :  
  
#### <a name="using-the-decision-tree-option-menus"></a>Utilisation des menus d'options d'arbre de décision  
  
1.  Cliquez sur le ruban **compléments** , puis affichez l’une des barres d’outils personnalisées utilisées pour travailler avec les diagrammes d’exploration de données :  
  
     **Disposition**  
     Optimise la disposition de l'arborescence pour qu'elle tienne sur la page active.  
  
     **Redimensionner la page**  
     Ce contrôle a été conçu pour les versions HTML antérieures. Utilisez plutôt les contrôles de redimensionnement de page Visio,  
  
     **Description**  
     Lorsqu'un nœud de l'arborescence est sélectionné, cliquez sur cette option pour afficher des détails sur les cas du nœud.  
  
2.  Utilisez l’option **redisposition** de la page du ruban **conception** de Visio pour expérimenter différentes dispositions d’arborescence.  
  
3.  Utilisez l’option **connecteurs** sous l’onglet **conception** pour modifier les connecteurs utilisés entre les nœuds dans l’arborescence.  
  
4.  Utilisez le contrôle **panoramique et zoom** , dans la zone **volet de tâches** du ruban **affichage** Visio, pour vous concentrer sur une zone particulière du diagramme.  
  
5.  Cliquez avec le bouton droit sur un nœud dans l'arborescence et faites un choix parmi ces options de menu contextuel spécifiques aux diagrammes d'arbre de décision :  
  
     **Améliorer la mise en page**  
     Répartit les nœuds équitablement sur la page et ajuste l'affichage de celle-ci pour présenter tous les nœuds.  
  
     **Déplacer les enfants vers la nouvelle page**  
     Déplace les enfants du nœud actuellement sélectionné vers une nouvelle page.  
  
     **Réduire les nœuds enfants**  
     Masque les enfants du nœud actuellement sélectionné.  
  
     **Développez les nœuds enfants**  
     Affiche les enfants du nœud sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des diagrammes d’exploration de données Visio &#40;SQL Server des compléments d’exploration de données&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
