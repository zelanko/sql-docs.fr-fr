---
title: Connecter des tâches et conteneurs à l’aide d’une contrainte de précédence par défaut | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- default precedence constraints
- containers [Integration Services], precedence constraints
ms.assetid: 8f31f15f-98ff-4c35-b41f-8b8cfd148d75
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a900b6c2bb6e55d57bcf32aff0ac6ea4667bdd7f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834051"
---
# <a name="connect-tasks-and-containers-by-using-a-default-precedence-constraint"></a>Connecter des tâches et des conteneurs à l'aide d'une contrainte de précédence par défaut
  Les contraintes de précédence connectent deux exécutables. Un exécutable peut être une tâche quelconque ou encore un conteneur de boucles For, de boucles Foreach ou un conteneur Sequence. Cette procédure décrit comment définir le comportement par défaut des contraintes de précédence et comment connecter des exécutables à l'aide de contraintes de précédence par défaut.  
  
## <a name="creating-default-precedence-constraints"></a>Création de contraintes de précédence par défaut  
 Lors de la première utilisation du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)], la valeur par défaut d'une contrainte de précédence est `Success`. Suivez les étapes ci-dessous pour configurer le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] de sorte qu'il utilise une valeur par défaut différente pour les contraintes de précédence.  
  
#### <a name="to-set-the-default-value-for-precedence-constraints"></a>Pour définir la valeur par défaut des contraintes de précédence  
  
1.  Ouvrez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Dans le menu **Outils** , cliquez sur **Options**.  
  
3.  Dans la boîte de dialogue **Options** , développez **Concepteurs Business Intelligence** , puis **Concepteurs de services d’intégration**.  
  
4.  Cliquez sur **Connexion automatique flux de contrôle** , puis sélectionnez **Connecter une nouvelle forme sur la forme sélectionnée par défaut**.  
  
5.  Dans la liste déroulante, choisissez **Utiliser une contrainte Failure (échec) pour la nouvelle forme** ou **Utiliser une contrainte Completion (fin) pour la nouvelle forme**.  
  
6.  Cliquez sur **OK**.  
  
#### <a name="to-create-a-default-precedence-constraint"></a>Pour créer une contrainte de précédence par défaut  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Sur la surface de dessin de l’onglet **Flux de contrôle** , cliquez sur la tâche ou le conteneur et faites glisser son connecteur vers l’exécutable auquel vous voulez que la contrainte de précédence s’applique.  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Contraintes de précédence](control-flow/precedence-constraints.md)   
 [Définissez la valeur d’une contrainte de précédence en utilisant le Menu contextuel](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Définir les propriétés d’une contrainte de précédence](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)   
 [Utiliser une expression dans une contrainte de précédence](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
