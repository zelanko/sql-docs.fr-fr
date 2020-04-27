---
title: Éditeur de tâche de transfert de travaux (page travaux) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.jobs.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 43066d036a23a063c218234b3a346bf89560994f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054990"
---
# <a name="transfer-jobs-task-editor-jobs-page"></a>Éditeur de tâche de transfert de travaux (page Travaux)
  Utilisez la page **Travaux** de la boîte de dialogue **Éditeur de tâche de transfert de travaux** pour spécifier les propriétés de copie d’un ou plusieurs travaux [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent d’une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à une autre. Pour plus d'informations sur la tâche de transfert de travaux, consultez [Transfer Jobs Task](control-flow/transfer-jobs-task.md).  
  
> [!NOTE]  
>  Pour accéder à des travaux sur le serveur source, les utilisateurs doivent au moins y être membres du rôle de base de données fixe **SQLAgentUserRole** . Pour créer des travaux sur le serveur de destination, l’utilisateur doit être membre du rôle serveur fixe **sysadmin** ou de l’un des rôles de base de données fixe de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent. Pour plus d’informations sur les rôles de base de données fixe de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent et leurs autorisations, consultez [Rôles de base de données fixe de l’Agent SQL Server](../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="options"></a>Options  
 **Abord SourceConnection**  
 Sélectionnez un gestionnaire de connexions Smo dans la liste ou cliquez sur ** \<nouvelle connexion... >** pour créer une connexion au serveur source.  
  
 **DestinationConnection**  
 Sélectionnez un gestionnaire de connexions Smo dans la liste ou cliquez sur ** \<nouvelle connexion... >** pour créer une connexion au serveur de destination.  
  
 **TransferAllJobs**  
 Déterminez si la tâche doit copier du serveur source au serveur de destination tous les travaux de l'Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou seulement ceux spécifiés.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**:**|Copie tous les travaux.|  
|**Fausses**|Copie uniquement les travaux spécifiés.|  
  
 **JobsList**  
 Cliquez sur le bouton Parcourir **(...)** pour sélectionner les travaux à copier. Un travail au moins doit être sélectionné.  
  
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
|**Saut**|La tâche ignore les travaux de même nom qui existent sur le serveur de destination.|  
  
 **EnableJobsAtDestination**  
 Déterminez si les travaux copiés sur le serveur de destination doivent être activés.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**:**|Active les travaux sur le serveur de destination.|  
|**Fausses**|Désactive les travaux sur le serveur de destination.|  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Tâches Integration Services](control-flow/integration-services-tasks.md)   
 [Éditeur de tâche de transfert de travaux &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Page expressions](expressions/expressions-page.md)   
 [Gestionnaire de connexions SMO](connection-manager/smo-connection-manager.md)  
  
  
