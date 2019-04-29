---
title: Déboguer un Package en définissant des points d’arrêt sur une tâche ou un conteneur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], breakpoints
- breakpoints [Integration Services]
- tasks [Integration Services], breakpoints
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3c78fb92078c604d881f18ea3472e23619771b49
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898887"
---
# <a name="debug-a-package-by-setting-breakpoints-on-a-task-or-a-container"></a>Déboguer un package en définissant des points d'arrêt sur une tâche ou un conteneur
  Cette section décrit la procédure de définition des points d'arrêt dans un package, une tâche, un conteneur de boucle For ou Foreach ou un conteneur de séquences.  
  
### <a name="to-set-breakpoints-in-a-package-a-task-or-a-container"></a>Pour définir des points d'arrêt dans un package, une tâche ou un conteneur  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Double-cliquez sur le package dans lequel vous souhaitez définir des points d'arrêt.  
  
3.  Dans le concepteur SSIS, effectuez les opérations suivantes :  
  
    -   Pour définir des points d’arrêt dans l’objet package, cliquez sur l’onglet **Flux de contrôle** , placez le curseur n’importe où sur l’arrière-plan de l’aire de conception, cliquez avec le bouton droit, puis cliquez sur **Modifier les points d’arrêt**.  
  
    -   Pour définir des points d’arrêt dans un flux de contrôle de package, cliquez sur l’onglet **Flux de contrôle** , cliquez avec le bouton droit sur une tâche, un conteneur de boucle For ou Foreach ou un conteneur de séquences, puis cliquez sur **Modifier les points d’arrêt**.  
  
    -   Pour définir des points d’arrêt dans un gestionnaire d’événements, cliquez sur l’onglet **Gestionnaire d’événements** , cliquez avec le bouton droit sur une tâche, un conteneur de boucle For ou Foreach ou un conteneur de séquences, puis cliquez sur **Modifier les points d’arrêt**.  
  
4.  Dans la boîte de dialogue **Définir les points d’arrêt de \<nom_conteneur>**, sélectionnez les points d’arrêt à activer.  
  
5.  Vous pouvez également modifier le type du nombre d'accès et la valeur du nombre d'accès pour chaque point d'arrêt.  
  
6.  Pour enregistrer le package, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de dépannage pour le développement des packages](troubleshooting/troubleshooting-tools-for-package-development.md)   
 [Déboguer un script en définissant des points d'arrêt dans une tâche de script et un composant de script](data-flow/transformations/script-component.md)   
 [Codage et débogage de la tâche de script](control-flow/script-task.md)   
 [Codage et débogage du composant Script](extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  
