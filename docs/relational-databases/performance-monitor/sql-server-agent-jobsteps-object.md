---
title: SQL Server Agent, objet JobSteps | Microsoft Docs
description: Découvrez l’objet de performance JobSteps de l’Agent SQL Server, qui contient des compteurs fournissant des informations sur les étapes des travaux SQL Server Agent.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 18c4c7db9fcd23581162eb4da4d763bfc1efbb3c
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505932"
---
# <a name="sql-server-agent-jobsteps-object"></a>SQL Server Agent, objet JobSteps
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  L'objet de performance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JobSteps **de l'Agent** intègre des compteurs de performances chargés de fournir des informations sur les étapes de travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le tableau ci-dessous répertorie les compteurs inclus dans cet objet.  
  
 Le tableau suivant énumère les compteurs **SQLAgent:JobSteps** .  
  
|Nom|Description|  
|----------|-----------------|  
|**Étapes actives**|Ce compteur fait état du nombre d'étapes de travail en cours d'exécution.|  
|**Étapes en attente**|Ce compteur fait état du nombre d'étapes de travail en mesure d'être exécutées par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mais dont l'exécution n'a pas encore commencé.|  
|**Total des tentatives d'exécution d'une étape**|Ce compteur indique le nombre de fois que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a retenté une étape de travail depuis le dernier redémarrage du serveur.|  
  
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
|**Fusionner**|Informations relatives aux étapes de travail qui utilisent le sous-système **Merge**|  
|**PowerShell**|Informations relatives aux étapes de travail qui utilisent le sous-système **PowerShell**|  
|**QueueReader**|Informations relatives aux étapes de travail qui utilisent le sous-système **QueueReader**|  
|**Instantané**|Informations relatives aux étapes de travail qui utilisent le sous-système **Snapshot**|  
|**TSQL**|Informations relatives aux étapes de travail qui exécutent [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les étapes de travail](../../ssms/agent/manage-job-steps.md)   
 [Utiliser des objets de performance](../../ssms/agent/use-performance-objects.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
