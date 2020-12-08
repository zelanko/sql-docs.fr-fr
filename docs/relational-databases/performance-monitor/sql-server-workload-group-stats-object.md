---
title: SQL Server, objet Workload Group Stats | Microsoft Docs
description: Découvrez l’objet SQLServer:Workload Group Stats, qui contient des compteurs de performances chargés de créer des rapports sur les statistiques des groupes de charges de travail de Resource Governor.
ms.custom: ''
ms.date: 12/04/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Workload Group Stats object
- 'SQLServer: Workload Group Stats'
ms.assetid: ca20e4f6-50ec-4456-900d-87d280fde2b3
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: cf82172eaa811d9992588e1615e55509c31be803
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505530"
---
# <a name="sql-server-workload-group-stats-object"></a>SQL Server, objet Workload Group Stats
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  L'objet SQLServer :Statistiques des groupes de charges de travail contient des compteurs de performance qui créent des rapports d'information sur les statistiques des groupes de charges de travail de Resource Governor.  
  
 Chaque groupe de charges de travail actif crée une instance de l'objet SQLServer : statistiques des groupes de charges de travail ayant le même nom d'instance que le nom de groupe de charges de travail de Resource Governor. Le tableau suivant décrit les compteurs pris en charge sur cette instance.  
  
|Nom du compteur|Description|  
|------------------|-----------------|  
|**Threads parallèles actifs**|Nombre actuel d'utilisations de threads parallèles.|  
|**Demandes actives**|Nombre de demandes qui sont en cours d'exécution dans ce groupe de charges de travail. Il doit être équivalent au nombre de lignes à partir de sys.dm_exec_requests filtrées par ID de groupe.|  
|**Demandes bloquées**|Nombre actuel de demandes bloquées dans le groupe de charges de travail. Peut être utilisé pour déterminer des caractéristiques de charge de travail.|  
|**% processeur retardé**|UC du système retardée pour toutes les demandes dans l’instance spécifiée de l’objet de performance, en pourcentage de la durée active totale.| 
|**Base de % processeur retardé**|À usage interne uniquement.| 
|**% processeur effectif**|Utilisation de l’UC système par toutes les demandes dans l’instance spécifiée de l’objet de performance, en pourcentage de la durée active totale.| 
|**Base de % processeur effectif**|À usage interne uniquement.| 
|**% d'utilisation de l'UC**|Utilisation de la bande passante de l'UC par toutes les demandes dans ce groupe de charges de travail évaluée en fonction de l'ordinateur et normalisée à tous les processeurs du système. Cette valeur se modifie selon la quantité d'UC disponible pour le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Elle n'est pas normalisée par rapport à ce que reçoit le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .| 
|**Base de % utilisation processeur**|À usage interne uniquement.| 
|**% non respecté**|Différence entre la réservation de l’UC et le pourcentage de planification effective.|  
|**Temps processeur max. par requête (ms)**|Temps processeur maximal, en millisecondes, utilisé par une demande en cours d'exécution dans le groupe de charges de travail.|  
|**Quantité max. de mémoire par requête (Ko)**|Valeur maximale de la quantité de mémoire, en kilo-octets (Ko), pour une requête.|  
|**Optimisations de requêtes/s**|Nombre des optimisations de requêtes qui se sont déroulées dans ce groupe de charges de travail par seconde. Peut être utilisé pour déterminer des caractéristiques de charge de travail.|  
|**Demandes en attente**|Nombre de demandes actuellement dans la file qui est en attente de sélection. Ce nombre peut être différent de zéro si la limitation se produit après que la limite GROUP_MAX_REQUESTS a été atteinte.|  
|**Nombre de requêtes à mémoire réduite/s**|Nombre de requêtes qui reçoivent une quantité réduite d'allocations de mémoire par seconde.|  
|**Demandes terminées/s**|Nombre de demandes qui sont terminées dans ce groupe de charges de travail. Ce nombre est cumulatif.|  
|**Plans non optimaux/s**|Nombre de plans non optimaux qui sont générés dans ce groupe de charges de travail par seconde.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQLServer, objet Statistiques des pools de ressources](../../relational-databases/performance-monitor/sql-server-resource-pool-stats-object.md)   
 [gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md)  
  
  
