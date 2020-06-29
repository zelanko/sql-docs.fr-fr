---
title: Conteneur d’hôte de tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4429d564cea0f08d5c2408199a8f1837b38389b0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438146"
---
# <a name="task-host-container"></a>conteneur d'hôte de tâche
  Le conteneur d'hôte de tâche encapsule une seule tâche. Dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , l'hôte de tâche n'est pas configuré séparément ; il est configuré lorsque vous définissez les propriétés de la tâche qu'il encapsule. Pour plus d'informations sur les tâches encapsulées par les conteneurs d’hôte de tâche, consultez [Tâches Integration Services](integration-services-tasks.md).  
  
 Ce conteneur étend l'utilisation des variables et des gestionnaires d'événements au niveau de la tâche. Pour plus d’informations, consultez [Gestionnaires d’événements Integration Services &#40;SSIS&#41; ](../integration-services-ssis-event-handlers.md) et [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
## <a name="configuration-of-the-task-host"></a>Configuration de l'hôte de tâche  
 Vous pouvez définir les propriétés dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou par programmation.  
  
 Pour plus d’informations sur la définition de ces propriétés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], consultez [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md).  
  
 Pour plus d’informations sur la définition par programmation de ces propriétés, consultez <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs Integration Services](integration-services-containers.md)  
  
  
