---
title: "T&#226;che de transfert de travaux | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transferjobstask.f1"
helpviewer_keywords: 
  - "tâche de transfert de travaux [Integration Services]"
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# T&#226;che de transfert de travaux
  La tâche de transfert de travaux transfère un ou plusieurs travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entre des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La tâche de transfert de travaux peut être configurée pour transférer tous les travaux ou seulement certains travaux spécifiés. Vous pouvez également spécifier si les travaux transférés sont activés lorsqu'ils arrivent à destination.  
  
 Les travaux à transférer peuvent déjà exister à l'emplacement de destination. La tâche de transfert de travaux peut être configurée pour traiter les travaux existants de différentes manières :  
  
-   Remplacer les travaux existants.  
  
-   Provoquer l'échec de la tâche lorsque des travaux dupliqués existent.  
  
-   Ignorer les travaux dupliqués.  
  
 À l'exécution, la tâche de transfert de travaux se connecte aux serveurs source et destination en utilisant un ou deux gestionnaires de connexions SMO. Le gestionnaire de connexions SMO est configuré indépendamment de la tâche de transfert de travaux, puis il est référencé dans celle-ci. Le gestionnaire de connexions SMO spécifie le serveur et le mode d'authentification à utiliser lors de l'accès au serveur. Pour plus d'informations, consultez [SMO Connection Manager](../../integration-services/connection-manager/smo-connection-manager.md).  
  
## Transfert de travaux entre des instances de SQL Server  
 La tâche de transfert de travaux prend en charge une source et une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Chacune des versions peut être utilisée indifféremment comme source ou comme destination.  
  
## Événements  
 La tâche de transfert de travaux génère un événement d'information qui indique le nombre de travaux transférés et un événement d'avertissement quand un travail est remplacé. La tâche n'indique pas les stades intermédiaires de l'avancement du transfert de travaux ; elle ne signale qu'une réalisation à 0 % ou à 100 %.  
  
## Valeur d'exécution  
 La valeur d'exécution, définie dans la propriété **ExecutionValue** de la tâche, renvoie le nombre de travaux transférés. En affectant une variable définie par l’utilisateur à la propriété **ExecValueVariable** de la tâche de transfert de travaux, les informations sur le transfert de travaux deviennent accessibles aux autres objets du package. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) et [Utiliser des variables dans des packages](../Topic/Use%20Variables%20in%20Packages.md).  
  
## Entrées du journal  
 La tâche de transfert de travaux comporte les entrées du journal personnalisées suivantes :  
  
-   TransferJobsTaskStarTransferringObjects   Cette entrée du journal indique que le transfert a commencé. L'entrée du journal inclut l'heure de début.  
  
-   TransferJobsTaskFinishedTransferringObjects   Cette entrée du journal indique que le transfert est terminé. L'entrée du journal inclut l'heure de fin.  
  
 En outre, une entrée de journal pour l'événement **OnInformation** indique le nombre de travaux qui ont été transférés et une entrée de journal pour l'événement **OnWarning** est générée pour chaque travail remplacé à l'emplacement de destination.  
  
## Sécurité et autorisations  
 Pour transférer des travaux, l'utilisateur doit être un membre du rôle serveur fixe sysadmin ou de l'un des rôles de base de données fixes de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur la base de données msdb à la fois sur les instances source et destination de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Configuration de la tâche de transfert de travaux  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche de transfert de travaux &#40;page Général&#41;](../../integration-services/control-flow/transfer-jobs-task-editor-general-page.md)  
  
-   [Éditeur de tâche de transfert de travaux &#40;page Travaux&#41;](../../integration-services/control-flow/transfer-jobs-task-editor-jobs-page.md)  
  
-   [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask>  
  
## Tâches associées  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Voir aussi  
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flux de contrôle](../../integration-services/control-flow/control-flow.md)  
  
  