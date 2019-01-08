---
title: Gestionnaires d’événements Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, events
- run-time [Integration Services]
- SQL Server Integration Services packages, events
- event handlers [Integration Services], about event handlers
- events [Integration Services]
- packages [Integration Services], events
- event handlers [Integration Services]
- SSIS packages, events
- containers [Integration Services], events
- events [Integration Services], about events
ms.assetid: 6f60cf93-35dc-431c-908d-2049c4ab66ba
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3d7ea5c6424283bd7b8aaa44f8a026ea18a9db30
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52751121"
---
# <a name="integration-services-ssis-event-handlers"></a>Gestionnaires d'événements Integration Services (SSIS)
  Lors de l'exécution, les exécutables (packages, conteneurs de boucles Foreach, conteneurs de boucles For, conteneurs de séquences et conteneurs d'hôtes de tâches) déclenchent des événements. Par exemple, un événement OnError se déclenche lorsqu'une erreur se produit. Vous pouvez créer des gestionnaires d'événements personnalisés pour ces événements afin d'étendre les fonctionnalités des packages et les rendre plus faciles à gérer au moment de l'exécution. Les gestionnaires d'événements peuvent réaliser des tâches comme les suivantes :  
  
-   nettoyer l'emplacement de stockage des données temporaires une fois l'exécution d'un package ou d'une tâche terminée ;  
  
-   récupérer les informations système de manière à évaluer la disponibilité des ressources avant exécution d'un package ;  
  
-   actualiser les données d'une table en cas d'échec d'une recherche dans une table de référence ;  
  
-   envoyer un message électronique lorsqu'une erreur ou un avertissement se produit ou lorsqu'une tâche échoue.  
  
 Si un événement ne possède pas de gestionnaire d'événements, il est remonté au conteneur qui se trouve un niveau au-dessus dans la hiérarchie des conteneurs d'un package. Si ce conteneur possède un gestionnaire d'événements, ce dernier est exécuté en réponse à l'événement. Dans le cas contraire, l'événement est remonté au conteneur qui se trouve un niveau au-dessus dans la hiérarchie des conteneurs.  
  
 Le diagramme qui suit montre un package simple composé d'un conteneur de boucles For contenant une tâche d'exécution SQL.  
  
 ![Package, boucle For, hôte de tâche et tâche d’exécution SQL](media/mw-dts-eventhandlerpkg.gif "Package, boucle For, hôte de tâche et tâche d’exécution SQL")  
  
 Seul le package possède un gestionnaire d'événements (pour son événement `OnError`). Si une erreur se produit pendant l'exécution de la tâche d'exécution SQL, le gestionnaire d'événements `OnError` du package s'exécute. Le diagramme qui suit montre la séquence d'appels qui conduit à l'exécution du gestionnaire d'événements `OnError` du package.  
  
 ![Flux de gestionnaire d’événements](media/mw-dts-eventhandlers.gif "Flux de gestionnaire d’événements")  
  
 Les gestionnaires d'événements sont membres d'une collection de gestionnaires d'événements. Tous les conteneurs incluent cette collection. Si vous créez le package à l’aide du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , vous pouvez afficher les membres des collections de gestionnaires d’événements dans les dossiers **Gestionnaires d’événements** de l’onglet **Explorateur de package** du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 Vous pouvez configurer le conteneur du gestionnaire d'événements de plusieurs manières :  
  
-   indiquez le nom et la description du gestionnaire d'événements ;  
  
-   indiquez si le gestionnaire d'événements s'exécute, si le package échoue en cas d'échec du gestionnaire d'événements et indiquez le nombre d'erreurs autorisées avant échec du gestionnaire d'événements ;  
  
-   spécifiez un résultat d'exécution à renvoyer à la place du résultat d'exécution réel renvoyé au moment de l'exécution par le gestionnaire d'événements ;  
  
-   spécifiez l'option de transaction du gestionnaire d'événements ;  
  
-   spécifiez le mode de journalisation utilisé par le gestionnaire d'événements.  
  
## <a name="event-handler-content"></a>Contenu du gestionnaire d'événements  
 La création d'un gestionnaire d'événements est similaire à la création d'un package. Un gestionnaire d'événements contient des tâches et des conteneurs qui sont mis en séquence de manière à former un flux de contrôle et peut inclure des flux de données. Le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] comprend un onglet **Gestionnaires d’événements** qui permet de créer des gestionnaires d’événements personnalisés. Pour plus d’informations, consultez [gestionnaires d’événements de Package SSIS](integration-services-ssis-event-handlers.md).  
  
 Vous pouvez également créer des gestionnaires d'événements par programme. Pour plus d’informations, consultez [Gestion des erreurs et des avertissements](building-packages-programmatically/handling-events-programmatically.md).  
  
## <a name="run-time-events"></a>Événements d'exécution  
 Le tableau qui suit énumère les gestionnaires d'événements fournis par [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et décrit les événements d'exécution provoquant leur exécution.  
  
|Gestionnaire d'événements|Événement|  
|-------------------|-----------|  
|`OnError`|Le Gestionnaire d’événements pour le `OnError` événement. Cet événement est déclenché par un exécutable lorsqu'une erreur se produit.|  
|**OnExecStatusChanged**|Gestionnaire d’événements de l’événement **OnExecStatusChanged** . Cet événement est déclenché par un exécutable lorsque son état d'exécution change.|  
|**OnInformation**|Gestionnaire d’événements de l’événement **OnInformation** . Cet événement se déclenche au cours de la validation et de l'exécution d'un exécutable afin de rapporter des informations. Cet événement véhicule des informations uniquement (aucune erreur ni avertissement).|  
|**OnPostExecute**|Gestionnaire d’événements de l’événement **OnPostExecute** . Cet événement est déclenché par un exécutable immédiatement après la fin de son exécution.|  
|**OnPostValidate**|Gestionnaire d’événements de l’événement **OnPostValidate** . Cet événement est déclenché par un exécutable lorsque sa validation est terminée.|  
|**OnPreExecute**|Gestionnaire d’événements de l’événement **OnPreExecute** . Cet événement est déclenché par un exécutable immédiatement avant son exécution.|  
|**OnPreValidate**|Gestionnaire d’événements de l’événement **OnPreValidate** . Cet événement est déclenché par un exécutable lorsque sa validation démarre.|  
|**OnProgress**|Gestionnaire d’événements de l’événement **OnProgress** . Cet événement est déclenché par un exécutable lorsqu'une progression mesurable est réalisée par l'exécutable.|  
|**OnQueryCancel**|Gestionnaire d’événements de l’événement **OnQueryCancel** . Cet événement est déclenché par un exécutable pour déterminer si son exécution doit s'arrêter.|  
|**OnTaskFailed**|Gestionnaire d’événements de l’événement **OnTaskFailed** . Cet événement est déclenché par une tâche lorsqu'elle échoue.|  
|**OnVariableValueChanged**|Gestionnaire d’événements de l’événement **OnVariableValueChanged** . Cet événement est déclenché par un exécutable lorsque la valeur d'une variable change. L'événement est déclenché par l'exécutable sur lequel la variable est définie. Cet événement n’est pas déclenché si vous définissez la **RaiseChangeEvent** propriété pour la variable à `False`. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md).|  
|**OnWarning**|Gestionnaire d’événements de l’événement **OnWarning** . Cet événement est déclenché par un exécutable lorsqu'un avertissement se produit.|  
  
## <a name="configuration-of-an-event-handler"></a>Configuration d'un gestionnaire d'événements  
 Vous pouvez définir les propriétés dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ou par programme.  
  
 Pour plus d’informations sur la définition de ces propriétés dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], consultez [Définir les propriétés d’une tâche ou d’un conteneur](../../2014/integration-services/set-the-properties-of-a-task-or-container.md).  
  
 Pour plus d'informations sur la définition par programmation de ces propriétés, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>.  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur l’ajout d’un gestionnaire d’événements à un package, consultez [Ajouter un gestionnaire d’événements à un package](../../2014/integration-services/add-an-event-handler-to-a-package.md).  
  
  
