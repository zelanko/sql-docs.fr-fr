---
title: SQL Server Agent, objet JobSteps | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 449c33bd69ffa4cb90ae4b65265f2c349ef32152
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158827"
---
# <a name="sql-server-agent-jobsteps-object"></a>SQL Server Agent, objet JobSteps
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'objet de performance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JobSteps **de l'Agent** intègre des compteurs de performances chargés de fournir des informations sur les étapes de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le tableau ci-dessous répertorie les compteurs inclus dans cet objet.  
  
 Le tableau suivant énumère les compteurs **SQLAgent:JobSteps** .  
  
|Nom   |Description|  
|----------|-----------------|  
|**Étapes actives**|Ce compteur fait état du nombre d'étapes de travail en cours d'exécution.|  
|**Étapes en attente**|Ce compteur fait état du nombre d'étapes de travail en mesure d'être exécutées par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mais dont l'exécution n'a pas encore commencé.|  
|**Total des tentatives d'exécution d'une étape**|Ce compteur indique le nombre de fois que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a tenté d'exécuter une étape de travail depuis le dernier redémarrage du serveur.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Instance|Description|  
|--------------|-----------------|  
|**_Total**|Informations relatives à toutes les étapes de travail|  
|**ActiveScripting**|Informations relatives aux étapes de travail qui utilisent le sous-système **ActiveScripting**|  
|**ANALYSISCOMMAND**|Informations relatives aux étapes de travail qui utilisent le sous-système ANALYSISCOMMAND|  
|**ANALYSISQUERY**|Informations relatives aux étapes de travail qui utilisent le sous-système ANALYSISQUERY|  
|**CmdExec**|Informations relatives aux étapes de travail qui utilisent le sous-système **CmdExec**|  
|**Distribution**|Informations relatives aux étapes de travail qui utilisent le sous-système **Distribution**|  
|**Dts**|Informations relatives aux étapes de travail qui utilisent le sous-système [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|  
|**LogReader**|Informations relatives aux étapes de travail qui utilisent le sous-système **LogReader**|  
|**Fusion**|Informations relatives aux étapes de travail qui utilisent le sous-système **Merge**|  
|**PowerShell**|Informations relatives aux étapes de travail qui utilisent le sous-système **PowerShell**|  
|**QueueReader**|Informations relatives aux étapes de travail qui utilisent le sous-système **QueueReader**|  
|**Snapshot**|Informations relatives aux étapes de travail qui utilisent le sous-système **Snapshot**|  
|**TSQL**|Informations relatives aux étapes de travail qui exécutent [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## <a name="see-also"></a> Voir aussi  
 [Gérer les étapes de travail](../../ssms/agent/manage-job-steps.md)   
 [Utiliser des objets de performance](../../ssms/agent/use-performance-objects.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
