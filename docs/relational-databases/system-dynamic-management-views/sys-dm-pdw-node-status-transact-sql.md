---
description: sys. dm_pdw_node_status (Transact-SQL)
title: sys. dm_pdw_node_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8e263b65-81d0-49d0-8873-62ef424369d6
author: markingmyname
ms.author: maghan
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fbe3aae7c707d836bafff703c8e86adffe4d1cd9
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89531106"
---
# <a name="sysdm_pdw_node_status-transact-sql"></a>sys. dm_pdw_node_status (Transact-SQL)

[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Contient des informations supplémentaires (sur [sys. dm_pdw_nodes &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)) sur les performances et l’état de tous les nœuds d’appliance. Elle répertorie une ligne par nœud dans l’appliance.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|ID numérique unique associé au nœud.<br /><br /> Clé pour cette vue.|Unique sur l’ensemble de l’appliance, quel que soit le type.|  
|process_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|process_name|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|allocated_memory|**bigint**|Mémoire allouée totale sur ce nœud.||  
|available_memory|**bigint**|Quantité totale de mémoire disponible sur ce nœud.||  
|process_cpu_usage|**bigint**|Utilisation totale du processeur, en graduations.||  
|total_cpu_usage|**bigint**|Utilisation totale du processeur, en graduations.||  
|thread_count|**bigint**|Nombre total de threads en cours d’utilisation sur ce nœud.||  
|handle_count|**bigint**|Nombre total de handles en cours d’utilisation sur ce nœud.||  
|total_elapsed_time|**bigint**|Temps total écoulé depuis le démarrage ou le redémarrage du système.|Temps total écoulé depuis le démarrage ou le redémarrage du système. Si total_elapsed_time dépasse la valeur maximale d’un entier (24,8 jours en millisecondes), cela entraînera un échec de matérialisation en raison d’un dépassement de capacité.<br /><br /> La valeur maximale en millisecondes est équivalente à 24,8 jours.|  
|is_available|**bit**|Indicateur précisant si ce nœud est disponible.||  
|sent_time|**datetime**|Dernière fois qu’un package réseau a été envoyé par ce nœud.||  
|received_time|**datetime**|Heure de la dernière réception d’un package réseau par ce nœud.||  
|error_id|**nvarchar (36)**|Identificateur unique de la dernière erreur qui s’est produite sur ce nœud.||  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
