---
title: "T&#226;che de transfert de proc&#233;dures stock&#233;es de master | Microsoft Docs"
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
  - "sql13.dts.designer.transfermasterspstask.f1"
helpviewer_keywords: 
  - "tâche de transfert de procédures stockées de master [Integration Services]"
ms.assetid: 81702560-48a3-46d1-a469-e41304c7af8e
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# T&#226;che de transfert de proc&#233;dures stock&#233;es de master
  La tâche de transfert de procédures stockées de master transfère une ou plusieurs procédures stockées définies par l’utilisateur entre les bases de données **master** sur des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour transférer une procédure stockée à partir de la base de données **master**, le propriétaire de la procédure doit être dbo.  
  
 La tâche de transfert de procédures stockées de master peut être configurée pour transférer toutes les procédures stockées ou seulement des procédures spécifiées. Cette tâche ne copie pas les procédures stockées système.  
  
 Les procédures stockées de master à transférer peuvent déjà exister à l'emplacement de destination. La tâche de transfert de procédures stockées de master peut être configurée pour traiter les procédures stockées existantes de différentes façons :  
  
-   Remplacer les procédures stockées existantes.  
  
-   Provoquer l'échec de la tâche lorsque des procédures stockées dupliquées existent.  
  
-   Ignorer les procédures stockées dupliquées.  
  
 À l'exécution, la tâche de transfert des procédures stockées de master se connecte aux serveurs source et destination en utilisant deux gestionnaires de connexions SMO. Les gestionnaires de connexions SMO sont configurés indépendamment de la tâche de transfert des procédures stockées de master, puis référencés dans celle-ci. Les gestionnaires de connexions SMO spécifient le serveur et le mode d'authentification à utiliser lors de l'accès au serveur. Pour plus d'informations, consultez [SMO Connection Manager](../../integration-services/connection-manager/smo-connection-manager.md).  
  
## Transfert de procédures stockées entre des instances de SQL Server  
 La tâche de transfert de procédures stockées de master prend en charge une source et une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Événements  
 La tâche génère un événement d'information qui indique le nombre de procédures stockées transférées et un événement d'avertissement lorsque qu'une procédure stockée est remplacée.  
  
 La tâche de transfert des procédures stockées de master n'indique pas les stades intermédiaires de l'avancement du transfert des connexions : elle signale la tâche comme réalisée à 0 % ou à 100 %.  
  
## Valeur d'exécution  
 La valeur d’exécution, définie dans la propriété **ExecutionValue** de la tâche, renvoie le nombre de procédures stockées transférées. En affectant une variable définie par l’utilisateur à la propriété **ExecValueVariable** de la tâche de transfert des procédures stockées de master, les informations sur le transfert des procédures stockées peuvent être rendues disponibles aux autres objets du package. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) et [Utiliser des variables dans des packages](../Topic/Use%20Variables%20in%20Packages.md).  
  
## Entrées du journal  
 La tâche de transfert des procédures stockées comporte les entrées de journal personnalisées suivantes :  
  
-   TransferStoredProceduresTaskStartTransferringObjects Cette entrée du journal indique que le transfert a commencé. L'entrée du journal inclut l'heure de début.  
  
-   TransferSStoredProceduresTaskFinishedTransferringObjects Cette entrée du journal indique que le transfert est terminé. L'entrée du journal inclut l'heure de fin.  
  
 En outre, une entrée de journal pour l’événement **OnInformation** indique le nombre de procédures stockées qui ont été transférées et une entrée de journal pour l’événement **OnWarning** est générée pour chaque procédure stockée remplacée à l’emplacement de destination.  
  
## Sécurité et autorisations  
 L’utilisateur doit avoir l’autorisation d’afficher la liste des procédures stockées dans la base de données **master** sur la source et doit être un membre du rôle serveur sysadmin ou disposer de l’autorisation de créer des procédures stockées dans la base de données **master** sur le serveur de destination.  
  
## Configuration de la tâche de transfert de procédures stockées de master  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche de transfert de procédures stockées de master &#40;page Général&#41;](../../integration-services/control-flow/transfer-master-stored-procedures-task-editor-general-page.md)  
  
-   [Éditeur de tâche de transfert de procédures stockées de master &#40;page Procédures stockées&#41;](../../integration-services/control-flow/transfer-master-stored-procedures-task-editor-stored-procedures-page.md)  
  
-   [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferStoredProceduresTask.TransferStoredProceduresTask>  
  
### Configuration par programmation de la tâche de transfert de procédures stockées de master  
  
## Tâches associées  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Voir aussi  
 [Tâche de transfert d'objets SQL Server](../../integration-services/control-flow/transfer-sql-server-objects-task.md)   
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flux de contrôle](../../integration-services/control-flow/control-flow.md)  
  
  