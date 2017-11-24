---
title: "Conteneur d’hôte de tâche | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 27fc5684d3ed15dcd8638e0515af57f7164d6e9c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="task-host-container"></a>conteneur d'hôte de tâche
  Le conteneur d'hôte de tâche encapsule une seule tâche. Dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , l'hôte de tâche n'est pas configuré séparément ; il est configuré lorsque vous définissez les propriétés de la tâche qu'il encapsule. Pour plus d'informations sur les tâches encapsulées par les conteneurs d’hôte de tâche, consultez [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md).  
  
 Ce conteneur étend l'utilisation des variables et des gestionnaires d'événements au niveau de la tâche. Pour plus d’informations, consultez [Gestionnaires d’événements Integration Services &#40;SSIS&#41; ](../../integration-services/integration-services-ssis-event-handlers.md) et [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md).  
  
## <a name="configuration-of-the-task-host"></a>Configuration de l'hôte de tâche  
 Vous pouvez définir les propriétés dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou par programmation.  
  
 Pour plus d’informations sur la définition de ces propriétés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], consultez [Définir les propriétés d’une tâche ou d’un conteneur](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b).  
  
 Pour plus d’informations sur la définition par programmation de ces propriétés, consultez <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Définir les propriétés d’une tâche ou d’un conteneur](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs Integration Services](../../integration-services/control-flow/integration-services-containers.md)  
  
  

