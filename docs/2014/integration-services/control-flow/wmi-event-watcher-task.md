---
title: Observateur d’événement WMI, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.wmieventwatchertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Event Watcher task [Integration Services]
ms.assetid: b5bb52e9-a77e-41e1-93f9-d4c3bc6b2c9a
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6e56f807e6f0d1bc7155c71d1332e56124b17da9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051574"
---
# <a name="wmi-event-watcher-task"></a>Tâche Observateur d'événement WMI
  La tâche Observateur d'événement WMI observe les événements WMI (Windows Management Instrumentation) à l'aide d'une requête d'événement WQL (Windows Management Instrumentation Query Language) pour spécifier les événements dignes d'intérêt. Vous pouvez utiliser la tâche Observateur d'événement WMI pour effectuer les opérations suivantes :  
  
-   Attendre la notification signalant que des fichiers ont été ajoutés à un dossier, puis initier le traitement du fichier.  
  
-   Exécuter un package qui supprime des fichiers lorsque la mémoire disponible sur un serveur tombe en deçà d'un pourcentage spécifique.  
  
-   Observer l'installation d'une application, puis exécuter un package qui utilise cette application.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut une tâche qui lit les informations WMI.  
  
 Pour plus d'informations sur cette tâche, cliquez sur la rubrique suivante :  
  
-   [Tâche Lecteur de données WMI](wmi-data-reader-task.md)  
  
## <a name="wql-queries"></a>Requêtes WQL  
 WQL est un dialecte de SQL avec des extensions qui permettent de prendre en charge la notification d'événement WMI et d'autres fonctionnalités spécifiques à WMI. Pour plus d’informations sur WQL, consultez la documentation Windows Management Instrumentation dans [MSDN Library](http://go.microsoft.com/fwlink/?linkid=62553).  
  
> [!NOTE]  
>  Les classes WMI varient d'une version de Windows à l'autre.  
  
 La requête suivante observe la notification signalant que l'utilisation du processeur est supérieure à 40 %.  
  
```  
SELECT * from __InstanceModificationEvent WITHIN 2 WHERE TargetInstance ISA 'Win32_Processor' and TargetInstance.LoadPercentage > 40  
```  
  
 La requête suivante observe la notification signalant qu'un fichier a été ajouté à un dossier.  
  
```  
SELECT * FROM __InstanceCreationEvent WITHIN 10 WHERE TargetInstance ISA "CIM_DirectoryContainsFile" and TargetInstance.GroupComponent= "Win32_Directory.Name=\"c:\\\\WMIFileWatcher\""   
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-event-watcher-task"></a>Messages de journalisation personnalisés disponibles dans la tâche Observateur d'événement WMI  
 Le tableau suivant répertorie les entrées de journal personnalisées de la tâche Observateur d'événement WMI. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|Indique qu'un événement surveillé par la tâche s'est produit.|  
|`WMIEventWatcherTimedout`|Indique que le délai de la tâche a expiré.|  
|`WMIEventWatcherWatchingForWMIEvents`|Indique que la tâche a commencé l'exécution de la requête WQL. L'entrée inclut la requête.|  
  
## <a name="configuration-of-the-wmi-event-watcher-task"></a>Configuration de la tâche Observateur d'événement WMI  
 Vous pouvez configurer la tâche Lecteur de données WMI de plusieurs manières :  
  
-   Spécifiez le gestionnaire de connexions WMI à utiliser.  
  
-   Spécifiez la source de la requête WQL. Celle-ci peut être externe à la tâche, une variable ou un fichier, ou la requête peut être stockée dans une propriété de tâche.  
  
-   Spécifiez l'action exécutée par la tâche lorsque l'événement WMI se produit. Vous pouvez enregistrer la notification d'événement et l'état après l'événement ou déclencher des événements [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] personnalisés qui fournissent des informations associées à l'événement WMI, à la notification et à l'état après l'événement.  
  
-   Définissez la manière dont la tâche répond à l'événement. La tâche peut être configurée de façon à réussir ou à échouer, selon l'événement, ou elle peut simplement observer encore l'événement.  
  
-   Spécifiez l'action exécutée par la tâche lorsque le délai d'attente de requête WMI arrive à expiration. Vous pouvez enregistrer le délai d’attente et l’état après le délai d’attente ou bien déclencher un événement [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] personnalisé, indiquant que l’événement WMI a dépassé le délai d’attente, et enregistrant le délai d’attente et l’état après le délai d’attente.  
  
-   Définissez la manière dont la tâche répond au délai d'attente. La tâche peut être configurée de façon à réussir ou à échouer, ou elle peut simplement observer encore l'événement.  
  
-   Spécifiez le nombre de fois où la tâche observe l'événement.  
  
-   Spécifiez le délai d'attente.  
  
 Si la source est un fichier, la tâche Observateur d'événement WMI utilise un gestionnaire de connexions de fichiers pour se connecter au fichier. Pour plus d'informations, consultez [Flat File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 La tâche Observateur d'événement WMI utilise un gestionnaire de connexions WMI pour se connecter au serveur à partir duquel elle lit les informations WMI. Pour plus d'informations, consultez [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche Observateur d’événement WMI &#40;Page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur de tâche Observateur d’événement WMI &#40;Page d’Options WMI&#41;](../wmi-event-watcher-task-editor-wmi-options-page.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-wmi-event-watcher-task"></a>Configuration par programmation de la tâche Observateur d'événement WMI  
 Pour plus d'informations sur la définition par programme de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiEventWatcherTask.WmiEventWatcherTask>  
  
  