---
title: SQL Server Agent, objet Alerts | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4b477d24172655ff459136bab58af76b5a542f1b
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-agent-alerts-object"></a>SQL Server Agent, objet Alerts
  L'objet de performance **Alerts** de SQL Server Agent contient des compteurs de performance qui donnent des informations sur les alertes de SQL Server Agent. Le tableau ci-dessous répertorie les compteurs inclus dans cet objet.  
  
 Le tableau suivant contient les compteurs **SQLAgent:Alerts** .  
  
|Nom|Description|  
|----------|-----------------|  
|**Alertes activées**|Ce compteur donne le nombre total d'alertes que SQL Server Agent a activées depuis son dernier redémarrage.|  
|**Alertes activées/minute**|Ce compteur donne le nombre d'alertes que SQL Server Agent a activées au cours de la dernière minute.|  
  
> [!NOTE]  
>  Pour utiliser cet objet de SQL Server Agent, les utilisateurs doivent être membres du rôle de serveur fixe **sysadmin**.  
  
## <a name="see-also"></a>Voir aussi  
 [Alertes](http://msdn.microsoft.com/library/3f57d0f0-4781-46ec-82cd-b751dc5affef)   
 [Utiliser des objets de performance](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
