---
title: SQL Server Agent, objet Alerts | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
caps.latest.revision: 24
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d310d463d0cb20135b1318f6ffd27c0b602f33e4
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40406611"
---
# <a name="sql-server-agent-alerts-object"></a>SQL Server Agent, objet Alerts
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'objet de performance **Alerts** de l'Agent SQL Server contient des compteurs de performance qui donnent des informations sur les alertes de l'Agent SQL Server. Le tableau ci-dessous répertorie les compteurs inclus dans cet objet.  
  
 Le tableau suivant contient les compteurs **SQLAgent:Alerts** .  
  
|Nom   |Description|  
|----------|-----------------|  
|**Alertes activées**|Ce compteur donne le nombre total d'alertes que l'Agent SQL Server a activées depuis son dernier redémarrage.|  
|**Alertes activées/minute**|Ce compteur donne le nombre d'alertes que l'Agent SQL Server a activées au cours de la dernière minute.|  
  
> [!NOTE]  
>  Pour utiliser cet objet de l’Agent SQL Server, les utilisateurs doivent être membres du rôle de serveur fixe **sysadmin** .  
  
## <a name="see-also"></a> Voir aussi  
 [Alertes](../../ssms/agent/alerts.md)   
 [Utiliser des objets de performance](../../ssms/agent/use-performance-objects.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
