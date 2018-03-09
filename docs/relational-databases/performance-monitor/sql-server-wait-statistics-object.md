---
title: SQL Server, objet Wait Statistics | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86fed40dbd12e7124aa837b7e428af711e33ef24
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-wait-statistics-object"></a>SQL Server, objet Wait Statistics
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] L’objet de performance **SQLServer:Wait Statistics** contient des compteurs de performances qui créent des rapports d’information sur l’état d’attente.  
  
 Le tableau ci-dessous répertorie les compteurs contenus dans l'objet Wait Statistics.  
  
|Compteurs Statistiques d'attente de SQL Server|Description|  
|-----------------------------------------|-----------------|  
|**Attente de verrouillage**|Statistiques des processus attendant un verrou.|  
|**Attente accès tampon journal**|Statistiques des processus attendant qu'un tampon journal soit disponible.|  
|**Attente d'écriture du journal**|Statistiques des processus attendant qu'un tampon journal soit écrit.|  
|**Attente d'allocation de mémoire**|Statistiques des processus attendant qu'une allocation de mémoire devienne disponible.|  
|**Attente d'E/S réseau**|Statistiques concernant l'attente sur l'E/S réseau.|  
|**Attente verrous non spécifiques des pages**|Statistiques concernant les verrous non spécifiques des pages.|  
|**Attente de verrous d'E/S de pages**|Statistiques concernant les verrous d'E/S de pages.|  
|**Attente de verrous de pages**|Statistiques concernant les verrous de pages, qui n'incluent pas les verrous d'E/S.|  
|**Attente d'objets mémoire thread-safe**|Statistiques relatives aux processus en attente d'allocateurs de mémoire thread-safe.|  
|**Attente de propriété de transaction**|Statistiques relatives aux processus de synchronisation d'accès à une transaction.|  
|**Attente du thread de travail**|Statistiques relatives aux processus en attente d'accès à un thread de travail.|  
|**Attente de synchronisation d'espace de travail**|Statistiques relatives aux processus de synchronisation d'accès à un espace de travail.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Élément|Description|  
|----------|-----------------|  
|**Temps d'attente moyen (ms)**|Temps moyen pour le type d'attente sélectionné.|  
|**Temps d'attente cumulé (ms) par seconde**|Temps d'attente agrégé par seconde, pour le type d'attente sélectionné.|  
|**Attentes en cours**|Nombre de processus en cours d'attente du type suivant.|  
|**Attentes démarrées par seconde**|Nombre d'attentes démarrées par seconde pour le type d'attente sélectionné.|  
  
## <a name="see-also"></a> Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
