---
title: Sys.dm_pdw_node_status (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8e263b65-81d0-49d0-8873-62ef424369d6
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 873f83991cbc89ff3e552646c04e8657b005181b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmpdwnodestatus-transact-sql"></a>Sys.dm_pdw_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contient des informations supplémentaires (via [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)) sur les performances et l’état de tous les nœuds de l’appliance. Il répertorie une ligne par un nœud dans l’appliance.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Id numérique unique associé au nœud.<br /><br /> Clé pour cette vue.|Le point d’entrée unique pour l’application, quel que soit le type.|  
|process_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|nom_processus|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|allocated_memory|**bigint**|Total alloué de la mémoire sur ce nœud.||  
|available_memory|**bigint**|Mémoire totale disponible sur ce nœud.||  
|process_cpu_usage|**bigint**|Utilisation de l’UC de processus totale, en graduations.||  
|total_cpu_usage|**bigint**|Utilisation du processeur total, en graduations.||  
|Thread_Count|**bigint**|Nombre total de threads en cours d’utilisation sur ce nœud.||  
|handle_count|**bigint**|Nombre total de handles en cours d’utilisation sur ce nœud.||  
|total_elapsed_time|**bigint**|Temps total écoulé depuis le système de démarrer ou redémarrer.|Temps total écoulé depuis le système de démarrer ou redémarrer. Si total_elapsed_time dépasse la valeur maximale pour un entier (24.8 jours en millisecondes), cela entraînera l’échec de matérialisation en raison d’un dépassement de capacité.<br /><br /> La valeur maximale, en millisecondes est équivalente à 24.8 jours.|  
|is_available|**bit**|Indicateur précisant si ce nœud est disponible.||  
|sent_time|**datetime**|Dernière heure d’un package de réseau a été envoyé par ce nœud.||  
|received_time|**datetime**|Dernière fois qu’un package de réseau a été reçu par ce nœud.||  
|error_id|**nvarchar(36)**|Identificateur unique de la dernière erreur qui s’est produite sur ce nœud.||  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les données en parallèle de l’entrepôt de vues de gestion dynamique &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
