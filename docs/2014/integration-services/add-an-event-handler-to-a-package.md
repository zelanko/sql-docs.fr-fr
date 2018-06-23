---
title: Ajoutez un gestionnaire d’événements à un Package | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- event handlers [Integration Services], creating
ms.assetid: 5e56885d-8658-480a-bed9-3f2f8003fd78
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 68d5ed9e638c03b1a34f221ff7e61d8a0df1a454
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041651"
---
# <a name="add-an-event-handler-to-a-package"></a>Ajouter un gestionnaire d'événements à un package
  Lors de l'exécution, les conteneurs et les tâches déclenchent des événements. Vous pouvez créer des gestionnaires d'événements personnalisés qui répondent à ces événements en exécutant un flux de travail. Vous pouvez ainsi créer un gestionnaire d'événements qui envoie un message électronique lorsqu'une tâche échoue.  
  
 Un gestionnaire d'événements est similaire à un package. Comme un package, il peut définir la portée des variables et inclure un flux de contrôle et des flux de données facultatifs. Vous pouvez créer des gestionnaires d'événements pour les packages, le conteneur de boucles Foreach, le conteneur de boucles For, le conteneur Sequence et toutes les tâches.  
  
 Vous pouvez pour cela utiliser l’aire de conception de l’onglet **Gestionnaires d’événements** du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 Quand l’onglet **Gestionnaires d’événements** est actif, les nœuds **Éléments de flux de contrôle** et **Tâches du plan de maintenance** de la Boîte à outils du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] contiennent la tâche et les conteneurs permettant de créer le flux de contrôle dans le gestionnaire d’événements. Les nœuds **Sources de flux de données**, **Transformations**et **Destinations du flux de données** contiennent les sources de données, les transformations et les destinations permettant de créer les flux de données dans le gestionnaire d’événements. Pour plus d’informations, consultez [Flux de contrôle](control-flow/control-flow.md) et [Flux de données](data-flow/data-flow.md).  
  
 L’onglet **Gestionnaires d’événements** contient aussi une zone **Gestionnaires de connexions** dans laquelle vous pouvez créer et modifier les gestionnaires de connexions utilisés par les gestionnaires d’événements pour se connecter aux serveurs et aux sources de données. Pour plus d’informations, consultez [Créer des gestionnaires de connexions](../../2014/integration-services/create-connection-managers.md).  
  
### <a name="to-create-an-event-handler"></a>Pour créer un gestionnaire d'événements  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Gestionnaires d’événements** .  
  
     ![Capture d’écran de l’aire de conception avec le gestionnaire d’événements](media/eventhandlers.gif "Capture d’écran de l’aire de conception avec le gestionnaire d’événements")  
  
     La création du flux de contrôle et des flux de données dans le gestionnaire d'événements est identique à la création du flux de contrôle et des flux de données dans un package. Pour plus d’informations, consultez [Flux de contrôle](control-flow/control-flow.md) et [Flux de données](data-flow/data-flow.md).  
  
4.  Dans la liste **Exécutable** , sélectionnez l’exécutable pour lequel vous voulez créer un gestionnaire d’événements.  
  
5.  Dans la liste **Gestionnaire d’événements** , sélectionnez le gestionnaire d’événements que vous voulez créer.  
  
6.  Cliquez sur le lien situé dans l’aire de conception de l’onglet **Gestionnaire d’événements** .  
  
7.  Ajoutez des éléments de flux de contrôle au gestionnaire d'événements et connectez ces éléments à l'aide d'une contrainte de priorité, en faisant glisser la contrainte d'un élément de flux de contrôle à l'autre. Pour plus d’informations, consultez [Control Flow](control-flow/control-flow.md).  
  
8.  Si vous le souhaitez, vous pouvez ajouter une tâche de flux de données puis, dans l’aire de conception de l’onglet **Flux de données** , créer un flux de données pour le gestionnaire d’événements. Pour en savoir plus, voir [Data Flow](data-flow/data-flow.md).  
  
9. Dans le menu **Fichier** , cliquez sur **Enregistrer les éléments sélectionnés** pour enregistrer le package.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Integration Services](../../2014/integration-services/sql-server-integration-services.md)   
 [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  