---
title: SQL Server Agent, objet JobSteps | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 323bf0c943d12a2d05e5fde80194d35d9ab733cf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206561"
---
# <a name="sql-server-agent-jobsteps-object"></a>SQL Server Agent, objet JobSteps
  L' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objet de performance **JobSteps** de l’agent contient des compteurs de performances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui signalent des informations sur les étapes de travail de l’agent. Le tableau ci-dessous répertorie les compteurs inclus dans cet objet.  
  
 Le tableau suivant énumère les compteurs **SQLAgent:JobSteps** .  
  
|Name|Description|  
|----------|-----------------|  
|**Étapes actives**|Ce compteur fait état du nombre d'étapes de travail en cours d'exécution.|  
|**Étapes en file d’attente**|Ce compteur fait état du nombre d'étapes de travail en mesure d'être exécutées par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mais dont l'exécution n'a pas encore commencé.|  
|**Nombre total de nouvelles tentatives d’étape**|Ce compteur indique le nombre total de tentatives [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’exécution d’une étape de travail depuis le dernier redémarrage du serveur.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Instance|Description|  
|--------------|-----------------|  
|**_Total**|Informations relatives à toutes les étapes de travail|  
|**ActiveScripting**|Informations relatives aux étapes de travail qui utilisent le sous-système **ActiveScripting**|  
|**ANALYSISCOMMAND**|Informations relatives aux étapes de travail qui utilisent le sous-système ANALYSISCOMMAND|  
|**ANALYSISQUERY**|Informations relatives aux étapes de travail qui utilisent le sous-système ANALYSISQUERY|  
|**CmdExec**|Informations relatives aux étapes de travail qui utilisent le sous-système **CmdExec**|  
|**Distribution**|Informations relatives aux étapes de travail qui utilisent le sous-système **Distribution**|  
|**DTS**|Informations relatives aux étapes de travail qui utilisent le sous-système [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|  
|**Lecteur**|Informations relatives aux étapes de travail qui utilisent le sous-système **LogReader**|  
|**Fusionner**|Informations relatives aux étapes de travail qui utilisent le sous-système **Merge**|  
|**PowerShell**|Informations relatives aux étapes de travail qui utilisent le sous-système **PowerShell**|  
|**QueueReader**|Informations relatives aux étapes de travail qui utilisent le sous-système **QueueReader**|  
|**Instantané**|Informations relatives aux étapes de travail qui utilisent le sous-système **Snapshot**|  
|**TSQL**|Informations relatives aux étapes de travail qui exécutent [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les étapes de travail](../../ssms/agent/manage-job-steps.md)   
 [Utiliser des objets de performance](../../ssms/agent/use-performance-objects.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
