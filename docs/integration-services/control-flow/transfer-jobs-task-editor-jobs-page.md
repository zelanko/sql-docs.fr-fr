---
title: "&#201;diteur de t&#226;che de transfert de travaux (page Travaux) | Microsoft Docs"
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
  - "sql13.dts.designer.transferjobstask.jobs.f1"
helpviewer_keywords: 
  - "Éditeur de tâche de transfert de travaux"
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# &#201;diteur de t&#226;che de transfert de travaux (page Travaux)
  Utilisez la page **Travaux** de la boîte de dialogue **Éditeur de tâche de transfert de travaux** pour spécifier les propriétés de copie d’un ou plusieurs travaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à une autre. Pour plus d'informations sur la tâche de transfert de travaux, consultez [Transfer Jobs Task](../../integration-services/control-flow/transfer-jobs-task.md).  
  
> [!NOTE]  
>  Pour accéder à des travaux sur le serveur source, les utilisateurs doivent au moins y être membres du rôle de base de données fixe **SQLAgentUserRole**. Pour créer des travaux sur le serveur de destination, l’utilisateur doit être membre du rôle serveur fixe **sysadmin** ou de l’un des rôles de base de données fixe de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Pour plus d’informations sur les rôles de base de données fixe de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent et leurs autorisations, consultez [Rôles de base de données fixe de l’Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## Options  
 **SourceConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur source.  
  
 **DestinationConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste, ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur de destination.  
  
 **TransferAllJobs**  
 Déterminez si la tâche doit copier du serveur source au serveur de destination tous les travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou seulement ceux spécifiés.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|Copie tous les travaux.|  
|**False**|Copie uniquement les travaux spécifiés.|  
  
 **JobsList**  
 Cliquez sur le bouton Parcourir **(…)** pour sélectionner les travaux à copier. Un travail au moins doit être sélectionné.  
  
> [!NOTE]  
>  Spécifiez **SourceConnection** avant de sélectionner les travaux à copier.  
  
 L’option **JobsList** n’est pas disponible quand **TransferAllJobs** a la valeur **True**.  
  
 **IfObjectExists**  
 Sélectionnez la façon dont la tâche doit gérer les travaux de même nom que ceux existant sur le serveur de destination.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**FailTask**|La tâche échoue si des travaux de même nom existent déjà sur le serveur de destination.|  
|**Remplacer**|La tâche remplace les travaux de même nom sur le serveur de destination.|  
|**Ignorer**|La tâche ignore les travaux de même nom qui existent sur le serveur de destination.|  
  
 **EnableJobsAtDestination**  
 Déterminez si les travaux copiés sur le serveur de destination doivent être activés.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|Active les travaux sur le serveur de destination.|  
|**False**|Désactive les travaux sur le serveur de destination.|  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Éditeur de tâche de transfert de travaux &#40;page Général&#41;](../../integration-services/control-flow/transfer-jobs-task-editor-general-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)   
 [Gestionnaire de connexions SMO](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  