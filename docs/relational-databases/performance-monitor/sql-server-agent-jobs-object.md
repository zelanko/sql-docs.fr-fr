---
title: SQL Server Agent, objet Jobs | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 077245e1ece089fa0a0b4ef98f2dd1fa6b9ec0d9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-agent-jobs-object"></a>Agent SQL Server, Objet Jobs
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] L’objet de performance **Jobs** de l’Agent SQL Server contient des compteurs qui fournissent des informations sur les travaux SQL Server Agent. Le tableau ci-dessous répertorie les compteurs inclus dans cet objet.  
  
 Le tableau ci-dessous contient les compteurs **SQLAgent:Jobs** .  
  
|Nom|Description|  
|----------|-----------------|  
|**Travaux actifs**|Nombre de travaux en cours d'exécution.|  
|**Travaux non réussis**|Nombre de travaux qui se sont terminés par un échec.|  
|**Taux de travaux réussis**|Pourcentage de travaux exécutés et terminés.|  
|**Travaux activés/minute**|Nombre de travaux lancés au cours de la dernière minute.|  
|**Travaux en attente**|Nombre de travaux prêts à l'exécution par l'Agent SQL Server, mais dont l'exécution n'a pas commencé.|  
|**Travaux réussis**|Nombre de travaux terminés.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Instance|Description|  
|--------------|-----------------|  
|**_Total**|Informations sur tous les travaux.|  
|**Alertes**|Informations sur les travaux lancés par des alertes.|  
|**Autres**|Informations sur les travaux qui n'ont pas été lancés par des alertes ou des planifications. Il s’agit généralement de travaux lancés manuellement au moyen de **sp_start_job**.|  
|**Planifications**|Informations sur les travaux lancés par des planifications.|  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter des travaux](http://msdn.microsoft.com/library/69e06724-25c7-4fb3-8a5b-3d4596f21756)   
 [Utiliser des objets de performance](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
