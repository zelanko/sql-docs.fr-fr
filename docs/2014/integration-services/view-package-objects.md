---
title: Afficher des objets de packages | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- Package Explorer window [Integration Services]
- packages [Integration Services], properties
- explorer view [Integration Services]
- SSIS packages, properties
- viewing package objects
- SQL Server Integration Services packages, properties
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 78a9b551ae44348de1c007533be3606b33c974cd
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58390087"
---
# <a name="view-package-objects"></a>Afficher des objets de packages
  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , l'onglet **Explorateur de package** fournit un aperçu du package. Cet affichage reflète la hiérarchie de conteneur de l'architecture [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Le conteneur de packages est situé en haut de la hiérarchie et vous pouvez développer le package pour afficher les connexions, les exécutables, les gestionnaires d'événements, les fournisseurs d'informations, les contraintes de précédence et les variables du package.  
  
 Les exécutables, qui sont les conteneurs et les tâches du package, peuvent inclure des gestionnaires d'événements, des contraintes de précédence et des variables. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] prend en charge une hiérarchie imbriquée de conteneurs, et les conteneurs de boucles For, de boucles Foreach et de séquences peuvent inclure d'autres exécutables.  
  
 Si un package contient un flux de données, l' **Explorateur de package** répertorie la tâche de flux de données et inclut un dossier **Composants** qui répertorie les composants du flux de données.  
  
 À partir de l'onglet **Explorateur de package** , vous pouvez supprimer des objets d'un package et accéder à la fenêtre **Propriétés** afin d'afficher les propriétés des objets.  
  
 Le schéma suivant illustre l'arborescence d'un package simple.  
  
 ![Capture d’écran de l’onglet Explorateur de package](media/packageexplorer.gif "Capture d’écran de l’onglet Explorateur de package")  
  
### <a name="to-view-package-content"></a>Pour afficher le contenu d'un package  
  
-   [Afficher les objets de package dans l’Explorateur de package](../../2014/integration-services/view-package-objects-in-package-explorer.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](control-flow/integration-services-tasks.md)   
 [Conteneurs Integration Services](control-flow/integration-services-containers.md)   
 [Contraintes de précédence](control-flow/precedence-constraints.md)   
 [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md)   
 [Gestionnaires d’événements Integration Services &#40;SSIS&#41;](integration-services-ssis-event-handlers.md)   
 [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
