---
description: Grouper ou dissocier des composants
title: Grouper ou dissocier des composants | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- grouping containers
- tasks [Integration Services], grouping
- containers [Integration Services], grouping
- grouping tasks
ms.assetid: 34320838-c271-4f8c-90b3-1254690890bb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7cd88383577694d5bef248baea5004056d239136
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "92195202"
---
# <a name="group-or-ungroup-components"></a>Grouper ou dissocier des composants

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


  Les onglets **Flux de contrôle**, **Flux de données** et **Gestionnaires d’événements** du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] prennent en charge le groupement réductible. Si un package contient plusieurs composants, les onglets peuvent être encombrés, ce qui rend difficile l'affichage simultané de tous les composants et la recherche de l'élément avec lequel vous souhaitez travailler. La fonctionnalité de groupement réductible permet d'économiser de l'espace sur la surface de travail et de faciliter l'utilisation des packages volumineux.  
  
 Vous sélectionnez les composants à grouper, vous les groupez, puis vous développez ou réduisez les groupes selon vos besoins. Le développement d'un groupe donne accès aux propriétés des composants du groupe. Les contraintes de précédence qui connectent les tâches et conteneurs sont incluses automatiquement dans le groupe.  
  
 Voici quelques observations concernant le regroupement des composants.  
  
-   Pour regrouper des composants, le flux de contrôle, le flux de données ou le gestionnaire d'événements doivent contenir plusieurs composants.  
  
-   Les groupes peuvent également être imbriqués, ce qui rend possible la création de groupes à l'intérieur d'autres groupes. La surface de dessin peut implémenter plusieurs groupes non imbriqués, mais un composant ne peut appartenir qu'à un seul groupe, à moins que les groupes soient imbriqués.  
  
-   Lors de l'enregistrement d'un package, le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] enregistre le groupement mais celui-ci n'a aucun effet sur l'exécution du package. La possibilité de grouper les composants est une fonctionnalité de conception ; elle n'affecte pas le comportement d'exécution du package.  
  
### <a name="to-group-components"></a>Pour regrouper des composants  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle**, **Flux de données** ou **Gestionnaires d’événements** .  
  
4.  Sur l’aire de conception de l’onglet, sélectionnez les composants que vous souhaitez grouper, cliquez avec le bouton droit sur un composant sélectionné, puis cliquez sur **Groupe**.  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### <a name="to-ungroup-components"></a>Pour dissocier des composants  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle**, **Flux de données** ou **Gestionnaires d’événements** .  
  
4.  Sur l’aire de conception de l’onglet, sélectionnez le groupe qui contient le composant que vous souhaitez dissocier, cliquez avec le bouton droit sur le composant sélectionné, puis cliquez sur **Dissocier**.  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Connecter des tâches et des conteneurs à l’aide d’une contrainte de précédence par défaut](./control-flow/precedence-constraints.md)  
  
