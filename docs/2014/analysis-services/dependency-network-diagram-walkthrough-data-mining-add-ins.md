---
title: Procédure pas à pas de dépendance réseau diagramme (compléments d’exploration de données) | Microsoft Docs
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
- Visio shapes, dependency network
- shapes, data mining
- shapes, network
- dependencies
- diagram, dependency network
- data mining layout toolbar
- dependency network
ms.assetid: aac732a8-5262-4649-b7d7-3ccf6f9cfa8b
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3efc5633a31af6d26fa7ae4abc5ce5b97f8542b1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218459"
---
# <a name="dependency-network-diagram-walkthrough-data-mining-add-ins"></a>Procédure pas à pas Diagramme Réseau de dépendances (Compléments d'exploration de données)
  Plusieurs types de modèles d'exploration de données différents utilisent un graphique de réseau comme manière d'explorer les relations dans les données. Vous pouvez importer ces modèles dans Visio à l’aide du **réseau de dépendances** mettre en forme, puis continuer de personnaliser et d’améliorer la disposition. Le **formes d’exploration de données pour Visio** incluent les contrôles personnalisés suivants pour travailler avec des diagrammes de réseau de dépendance :  
  
-   Contrôles de rendu du graphique de réseau  
  
     Ces options font partie de l'Assistant qui est exécuté lorsque vous déposez une forme dans l'espace de travail Visio.  
  
-   **Data Mining Layout** barre d’outils  
  
     Ces options sont ajoutées à l'espace de travail Visio pour vous aider à interagir avec le graphique de réseau de dépendances.  
  
## <a name="build-a-dependency-network-graph"></a>Créer un graphique de réseau de dépendances  
 Vous déposez une forme sur la page Visio pour lancer le **Assistant forme Visio réseau de dépendances** et définir les options du diagramme.  
  
#### <a name="use-the-dependency-net-visio-shape-wizard"></a>Utiliser l'Assistant Création de forme Réseau de dépendances Visio  
  
1.  Si vous ne voyez pas **formes d’exploration de données Microsoft** dans le **formes** , cliquez sur **formes plus**, sélectionnez **ouvrir un gabarit**, puis ouvrez le modèle à partir de l’emplacement d’installation par défaut.  
  
     \<lecteur > : \Program files (x85) \Microsoft SQL Server 2012 DM Add-Ins  
  
2.  Faites glisser le **réseau de dépendances** forme sur la page pour démarrer l’Assistant. Cliquez sur **Suivant**.  
  
3.  Sur la page d’accueil de la **Assistant Création de forme Visio dépendance réseau**, cliquez sur **suivant**.  
  
4.  Sur le **sélectionner une Source de données** page de la **Assistant Création de forme Visio dépendance réseau**, choisir une connexion à un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] serveur qui contient le modèle que vous souhaitez visualiser.  
  
5.  Sélectionnez un modèle d’exploration de données approprié, puis cliquez sur **suivant**.  
  
     Pour sélectionner un modèle adéquat, vous pouvez consulter le nom, description, colonnes et type de données dans le **propriétés** volet.  
  
     Cette forme prend en charge les modèles créés à l'aide des algorithmes suivants :  
  
    -   Naïve Bayes  
  
    -   Arbres de décision  
  
    -   Règles d'association  
  
6.  Dans la page, **sélectionnez les nœuds pour le rendu**, personnaliser la taille du graphique et éventuellement un filtre pour inclure uniquement certains nœuds.  
  
     Avec un jeu de données volumineux, un graphique de dépendance peut devenir encombrant et contenir de nombreux objets associés, représentés en tant que *nœuds*. En utilisant cette boîte de dialogue, vous pouvez créer un graphique de réseau personnalisé qui contient uniquement les nœuds dignes d'intérêt.  
  
     [espace réservé aux graphiques]  
  
     **Nombre de nœuds à extraire**  
     Si le modèle contient un nombre inférieur au nombre spécifié de nœuds, ce paramètre n'a aucun effet. Si le modèle contient un nombre de nœuds supérieur au nombre spécifié, seuls les nœuds les plus forts sont affichés.  
  
     **Le nom contient**  
     Laissez cette zone vide et cliquez sur la flèche verte pour extraire tous les nœuds du modèle.  
  
     Sinon, tapez une chaîne et cliquez sur la flèche verte pour retourner uniquement les nœuds qui contiennent la chaîne spécifiée.  
  
     La plupart des modèles que vous pouvez créer avec les exemples de données ne sont pas volumineux ; par conséquent, pour cet exemple, augmentez le nombre de nœuds à 10, puis cliquez sur la flèche verte pour exécuter une requête et obtenir la liste de tous les nœuds.  
  
7.  Cliquez sur **avancé** pour définir les options d’ombrage et de la forme du graphique.  
  
8.  Cliquez sur **fermer** pour quitter le **avancé** boîte de dialogue options, puis cliquez sur **Terminer** pour créer le graphique.  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Explorer et modifier le diagramme terminé  
 Une fois que Visio a créé le graphique de dépendances de réseau, vous pouvez continuer à modifier et à améliorer le graphique en utilisant les fonctionnalités de Visio.  
  
 Le graphique suivant montre la disposition par défaut d'un graphique de réseau de dépendances.  
  
 [espace réservé aux graphiques]  
  
1.  Utilisez le **panoramique et Zoom** contrôle, dans le **volet** zone de Visio **vue** ruban pour vous concentrer sur une section du graphique et vous déplacer dans le diagramme.  
  
2.  Faire des essais avec différentes dispositions de graphique fournie par le Visio **Redisposition** option.  
  
3.  Cliquez sur le **Add-Ins** ruban et afficher une barre d’outils personnalisées utilisées pour travailler avec des diagrammes d’exploration de données :  
  
     **Mise en page**  
     Optimise la disposition des nœuds sur la page et modifie l'affichage pour que tous les nœuds soient visibles.  
  
     **Redimensionner la Page**  
     Modifie la taille de la page pour que tous les nœuds soient visibles.  
  
     **Résistance du bord**  
     Fait basculer l'affichage de la résistance du bord de l'ensemble du graphique. Un bord représente une connexion entre des nœuds. Vous pouvez utiliser le curseur pour exclure les connexions qui ne sont pas fortes.  
  
     **Curseur**  
     Le **curseur** vous permet de contrôler la force des relations qui sont affichés dans le diagramme de réseau de dépendances.  
  
     Chaque nœud du graphique représente un état. Une flèche représente une transition entre deux états et la probabilité associée à la transition. Pour réduire le nombre de nœuds dans le graphique, déplacez le curseur vers le haut.  
  
     Pour augmenter le nombre de nœuds dans le graphique, déplacez le curseur vers le bas.  
  
     **Ajouter des éléments**  
     Ouvre le **sélectionnez les nœuds pour le rendu** boîte de dialogue afin que vous puissiez sélectionner les nouveaux nœuds à ajouter au graphique.  
  
4.  Vous pouvez créer des graphiques simples ou élaborés, à votre convenance, puis ajouter des annotations, tout en restant connecté au modèle.  
  
     [espace réservé aux graphiques]  
  
> [!WARNING]  
>  La mise en surbrillance des nœuds dépendants et d'autres options de menu contextuel qui étaient disponibles dans les versions précédentes des compléments ne fonctionnent pas dans Office 2013.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des diagrammes d’exploration de données Visio &#40;compléments d’exploration de données SQL Server&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
