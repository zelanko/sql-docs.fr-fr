---
title: SQL Server Agent, objet Alerts | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d55a1cb1e918dde94862202de0fa54aed5ff4d54
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158507"
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
  
  
