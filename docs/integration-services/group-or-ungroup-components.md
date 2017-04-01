---
title: "Grouper ou dissocier des composants | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "groupement de conteneurs"
  - "tâches [Integration Services], regroupement"
  - "conteneurs [Integration Services], regroupement"
  - "regroupement de tâches"
ms.assetid: 34320838-c271-4f8c-90b3-1254690890bb
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# Grouper ou dissocier des composants
  Les onglets **Flux de contrôle**, **Flux de données** et **Gestionnaires d’événements** du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] prennent en charge le groupement réductible. Si un package contient plusieurs composants, les onglets peuvent être encombrés, ce qui rend difficile l'affichage simultané de tous les composants et la recherche de l'élément avec lequel vous souhaitez travailler. La fonctionnalité de groupement réductible permet d'économiser de l'espace sur la surface de travail et de faciliter l'utilisation des packages volumineux.  
  
 Vous sélectionnez les composants à grouper, vous les groupez, puis vous développez ou réduisez les groupes selon vos besoins. Le développement d'un groupe donne accès aux propriétés des composants du groupe. Les contraintes de précédence qui connectent les tâches et conteneurs sont incluses automatiquement dans le groupe.  
  
 Voici quelques observations concernant le regroupement des composants.  
  
-   Pour regrouper des composants, le flux de contrôle, le flux de données ou le gestionnaire d'événements doivent contenir plusieurs composants.  
  
-   Les groupes peuvent également être imbriqués, ce qui rend possible la création de groupes à l'intérieur d'autres groupes. La surface de dessin peut implémenter plusieurs groupes non imbriqués, mais un composant ne peut appartenir qu'à un seul groupe, à moins que les groupes soient imbriqués.  
  
-   Lors de l'enregistrement d'un package, le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] enregistre le groupement mais celui-ci n'a aucun effet sur l'exécution du package. La possibilité de grouper les composants est une fonctionnalité de conception ; elle n'affecte pas le comportement d'exécution du package.  
  
### Pour regrouper des composants  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle**, **Flux de données** ou **Gestionnaires d’événements**.  
  
4.  Sur l’aire de conception de l’onglet, sélectionnez les composants que vous souhaitez grouper, cliquez avec le bouton droit sur un composant sélectionné, puis cliquez sur **Groupe**.  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### Pour dissocier des composants  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle**, **Flux de données** ou **Gestionnaires d’événements**.  
  
4.  Sur l’aire de conception de l’onglet, sélectionnez le groupe qui contient le composant que vous souhaitez dissocier, cliquez avec le bouton droit sur le composant sélectionné, puis cliquez sur **Dissocier**.  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## Voir aussi  
 [Ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Connecter des tâches et des conteneurs à l'aide d'une contrainte de précédence par défaut](../Topic/Connect%20Tasks%20and%20Containers%20by%20Using%20a%20Default%20Precedence%20Constraint.md)  
  
  