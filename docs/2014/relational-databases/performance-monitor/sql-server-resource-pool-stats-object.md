---
title: SQL Server, objet Resource Pool Stats | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Reosurce Pool Stats object
- 'SQLServer: Resource Pool Stats object'
ms.assetid: bb46e029-fcf9-4aeb-a066-be41e7668fb9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1c2ca8360e752146dac13e9cc6a3737ac2373cc9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066100"
---
# <a name="sql-server-resource-pool-stats-object"></a>SQLServer, objet Statistiques des pools de ressources
  L'objet SQLServer:Resource Pool Stat contient des compteurs de performance qui créent des rapports d'information sur les statistiques du pool des ressources de Resource Governor.  
  
 Chaque pool de ressources actif crée une instance de l'objet de performance SQLServer : Statistiques des pools de ressources (SQLServer:Resource Pool Stats) ayant le même nom d'instance que le nom du pool de ressources de Resource Governor. Le tableau suivant décrit les compteurs pris en charge sur cette instance.  
  
|Nom du compteur|Description|  
|------------------|-----------------|  
|% d'utilisation de l'UC|Utilisation de la bande passante de l'UC sur toutes les demandes dans tous les groupes de charges de travail qui appartiennent à ce pool. Elle est mesurée en fonction de l'ordinateur et normalisée à tous les processeurs du système. Cette valeur se modifie selon la quantité d'UC disponible pour le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Elle n'est pas normalisée par rapport à ce que reçoit le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|% cible de l'utilisation de l'UC|Valeur cible du pourcentage d'utilisation de l'UC pour le pool de ressources basée sur les paramètres de configuration du pool de ressources et de la charge du système.|  
|% d'effet de contrôle de l'UC|Effet de Resource Governor sur le pool de ressources. Calculé selon la formule (% d'utilisation de l'UC) / (% d'utilisation de l'UC sans Resource Governor).|  
|Cible mémoire pour la compilation (Ko)|Cible gestionnaire d'allocation mémoire actuelle, en kilo-octets (Ko), pour les compilations de requête.|  
|Cible mémoire pour le cache (Ko)|Cible gestionnaire d'allocation mémoire actuelle, en kilo-octets (Ko), pour le cache.|  
|Cible mémoire pour l'exécution de requêtes (Ko)|Cible gestionnaire d'allocation mémoire actuelle, en kilo-octets (Ko), pour l'allocation mémoire de l'exécution de requête. Ces informations sont également disponibles dans [sys.dm_exec_query_memory_grants](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql).|  
|Allocations de mémoire/s|Nombre d'allocations de mémoire qui se produisent dans ce pool de ressources par seconde.|  
|Nombre d'allocations de mémoire actives|Nombre total actuel d'allocations de mémoire. Ces informations sont également disponibles dans [sys.dm_exec_query_memory_grants](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql).|  
|Délais d'expiration des allocations de mémoire/s|Nombre de délais d'expiration des allocations de mémoire par seconde.|  
|Quantité d'allocation de mémoire active (Ko)|Quantité totale de mémoire actuellement allouée, en kilo-octets (Ko). Ces informations sont également disponibles dans [sys.dm_exec_query_resource_semaphores](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql).|  
|Nombre d'allocations de mémoire en attente|Nombre de demandes pour les allocations de mémoire en attente dans les files d'attente. Ces informations sont également disponibles dans [sys.dm_exec_query_resource_semaphores](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql).|  
|Mémoire max. (Ko)|Quantité maximale, en kilo-octets (Ko), de mémoire dont peut disposer le pool de ressources selon les paramètres du pool de ressources et l'état du serveur.|  
|Mémoire utilisée (Ko)|Quantité de mémoire utilisée, en kilo-octets (Ko), pour le pool de ressources.|  
|Mémoire cible (Ko)|Quantité cible, en kilo-octets (Ko), de mémoire que le pool de ressources tente d'obtenir selon les paramètres du pool de ressources et l'état du serveur.|  
|E/S de lecture sur le disque par seconde|Nombre d'opérations de lecture à partir du disque au cours de la dernière seconde.|  
|E/S de lecture sur le disque limitées par seconde|Nombre d'opérations de lecture limitées au cours de la dernière seconde.|  
|Nb d’octets de lecture de disque/s|Nombre d'octets lus à partir du disque au cours de la dernière seconde.|  
|Millisecondes moyennes par lecture depuis le disque|Durée moyenne, en millisecondes, d'une opération de lecture sur le disque.|  
|E/S d'écriture sur le disque par seconde|Nombre d'opérations d'écriture sur le disque au cours de la dernière seconde.|  
|E/S d'écriture sur le disque limitées par seconde|Nombre d'opérations d'écriture limitées au cours de la dernière seconde.|  
|Nb d’octets d’écriture de disque/s|Nombre d'octets écrits sur le disque au cours de la dernière seconde.|  
|Millisecondes moyennes par écriture sur le disque|Durée moyenne, en millisecondes, d'une opération d'écriture sur le disque.|  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, objet de statistiques de groupe de charges de travail](sql-server-workload-group-stats-object.md)   
 [gouverneur de ressources](../resource-governor/resource-governor.md)  
  
  
