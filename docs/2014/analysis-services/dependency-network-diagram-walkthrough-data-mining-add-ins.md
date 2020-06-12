---
title: Procédure pas à pas relative à un diagramme de réseau de dépendances (compléments d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8138cef980e7b040a99a6e1db21f1b67fd84aeb5
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528775"
---
# <a name="dependency-network-diagram-walkthrough-data-mining-add-ins"></a>Procédure pas à pas Diagramme Réseau de dépendances (Compléments d'exploration de données)
  Plusieurs types de modèles d'exploration de données différents utilisent un graphique de réseau comme manière d'explorer les relations dans les données. Vous pouvez importer ces modèles dans Visio à l’aide de la forme **réseau de dépendances** , puis continuer à personnaliser et améliorer la disposition. Les **formes d’exploration de données pour Visio** incluent les contrôles personnalisés suivants pour l’utilisation des diagrammes de réseau de dépendances :  
  
-   Contrôles de rendu du graphique de réseau  
  
     Ces options font partie de l'Assistant qui est exécuté lorsque vous déposez une forme dans l'espace de travail Visio.  
  
-   Barre d’outils de **disposition d’exploration de données**  
  
     Ces options sont ajoutées à l'espace de travail Visio pour vous aider à interagir avec le graphique de réseau de dépendances.  
  
## <a name="build-a-dependency-network-graph"></a>Créer un graphique de réseau de dépendances  
 Vous déposez une forme sur la page Visio pour lancer l' **Assistant Création de forme réseau de dépendances Visio** et définir les options du diagramme.  
  
#### <a name="use-the-dependency-net-visio-shape-wizard"></a>Utiliser l'Assistant Création de forme Réseau de dépendances Visio  
  
1.  Si les **formes d’exploration de données Microsoft** ne s’affichent pas dans la liste **formes** , cliquez sur **autres formes**, sélectionnez **ouvrir le stencil**, puis ouvrez le modèle à partir de l’emplacement d’installation par défaut.  
  
     \<drive>: \Program Files (x85) \Microsoft SQL Server 2012 DM Add-ins  
  
2.  Faites glisser la forme **réseau de dépendances** sur la page pour démarrer l’Assistant. Cliquez sur **Suivant**.  
  
3.  Sur la page d’accueil de l **'Assistant Création d’une forme réseau de dépendances Visio**, cliquez sur **suivant**.  
  
4.  Dans la page **Sélectionner une source de données** de l' **Assistant Création de forme réseau de dépendances Visio**, choisissez une connexion à un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] serveur qui possède le modèle que vous souhaitez visualiser.  
  
5.  Sélectionnez un modèle d’exploration de données approprié, puis cliquez sur **suivant**.  
  
     Pour sélectionner un modèle approprié, vous pouvez examiner le nom, la description, les colonnes et le type de données dans le volet **Propriétés** .  
  
     Cette forme prend en charge les modèles créés à l'aide des algorithmes suivants :  
  
    -   Naïve Bayes  
  
    -   Arbres de décision  
  
    -   Règles d'association  
  
6.  Sur la page, **sélectionnez les nœuds à afficher**, personnalisez la taille du graphique et, éventuellement, filtrez pour inclure uniquement certains nœuds.  
  
     Avec un jeu de données volumineux, un graphique de dépendance peut devenir énorme et contenir de nombreux objets associés, représentés sous forme de *nœuds*. En utilisant cette boîte de dialogue, vous pouvez créer un graphique de réseau personnalisé qui contient uniquement les nœuds dignes d'intérêt.  
  
     [espace réservé art]  
  
     **Nombre de nœud à extraire**  
     Si le modèle contient un nombre inférieur au nombre spécifié de nœuds, ce paramètre n'a aucun effet. Si le modèle contient un nombre de nœuds supérieur au nombre spécifié, seuls les nœuds les plus forts sont affichés.  
  
     **Le nom contient**  
     Laissez cette zone vide et cliquez sur la flèche verte pour extraire tous les nœuds du modèle.  
  
     Sinon, tapez une chaîne et cliquez sur la flèche verte pour retourner uniquement les nœuds qui contiennent la chaîne spécifiée.  
  
     La plupart des modèles que vous pouvez créer avec les exemples de données ne sont pas volumineux ; par conséquent, pour cet exemple, augmentez le nombre de nœuds à 10, puis cliquez sur la flèche verte pour exécuter une requête et obtenir la liste de tous les nœuds.  
  
7.  Cliquez sur **avancé** pour définir les options d’ombrage et de forme du graphique.  
  
8.  Cliquez sur **Fermer** pour quitter la boîte de dialogue Options **avancées** , puis cliquez sur **Terminer** pour créer le graphique.  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Explorer et modifier le diagramme terminé  
 Une fois que Visio a créé le graphique de dépendances de réseau, vous pouvez continuer à modifier et à améliorer le graphique en utilisant les fonctionnalités de Visio.  
  
 Le graphique suivant montre la disposition par défaut d'un graphique de réseau de dépendances.  
  
 [espace réservé art]  
  
1.  Utilisez le contrôle **panoramique et zoom** , dans la zone **volet de tâches** du ruban **affichage** Visio, pour vous concentrer sur une section du graphique et vous déplacer dans le diagramme.  
  
2.  Faites des essais avec différentes dispositions graphiques fournies par l’option de **page redisposition** Visio.  
  
3.  Cliquez sur le ruban **compléments** , puis affichez l’une des barres d’outils personnalisées utilisées pour travailler avec les diagrammes d’exploration de données :  
  
     **Disposition**  
     Optimise la disposition des nœuds sur la page et modifie l'affichage pour que tous les nœuds soient visibles.  
  
     **Redimensionner la page**  
     Modifie la taille de la page pour que tous les nœuds soient visibles.  
  
     **Résistance du bord**  
     Fait basculer l'affichage de la résistance du bord de l'ensemble du graphique. Un bord représente une connexion entre des nœuds. Vous pouvez utiliser le curseur pour exclure les connexions qui ne sont pas fortes.  
  
     **Curseur**  
     Le **curseur** vous permet de contrôler la force des relations affichées dans le diagramme du réseau de dépendances.  
  
     Chaque nœud du graphique représente un état. Une flèche représente une transition entre deux états et la probabilité associée à la transition. Pour réduire le nombre de nœuds dans le graphique, déplacez le curseur vers le haut.  
  
     Pour augmenter le nombre de nœuds dans le graphique, déplacez le curseur vers le bas.  
  
     **Ajouter des éléments**  
     Ouvre la boîte de dialogue **Sélectionner les nœuds à afficher** pour vous permettre de sélectionner de nouveaux nœuds à ajouter au graphique.  
  
4.  Vous pouvez créer des graphiques simples ou élaborés, à votre convenance, puis ajouter des annotations, tout en restant connecté au modèle.  
  
     [espace réservé aux graphiques]  
  
> [!WARNING]  
>  La mise en surbrillance des nœuds dépendants et d'autres options de menu contextuel qui étaient disponibles dans les versions précédentes des compléments ne fonctionnent pas dans Office 2013.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des diagrammes d’exploration de données Visio &#40;SQL Server des compléments d’exploration de données&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
