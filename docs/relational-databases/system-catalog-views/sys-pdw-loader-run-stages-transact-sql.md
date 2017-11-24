---
title: Sys.pdw_loader_run_stages (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 255681e9-323c-42c0-a63c-1f05536efdd5
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d209fff76a89f84b67e351864b102ebf8ecbcd5f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwloaderrunstages-transact-sql"></a>Sys.pdw_loader_run_stages (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contient des informations sur les opérations de chargement en cours et terminées dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Les informations sont conservées entre les redémarrages du système.  
  
|||||  
|-|-|-|-|  
|Nom de la colonne|Type de données| Description|Plage|  
|run_id|**int**|Identificateur unique d’un chargeur de s’exécuter.||  
|étape|**nvarchar (30)**|L’étape actuelle pour l’exécution.|'CREATE_STAGING', 'DMS_LOAD', 'LOAD_INSERT', 'LOAD_CLEANUP'|  
|request_id|**nvarchar(32)**|ID de la demande en cours d’exécution cette étape.||  
|status|**nvarchar(16)**|État de cette phase.||  
|start_time|**datetime**|Heure de début de l’étape.||  
|end_time|**datetime**|Heure à laquelle l’étape s’est terminée, le cas échéant.|NULL si non démarré ou en cours d’exécution.|  
|total_elapsed_time|**int**|Temps total ce stade passé (ou passé jusqu'à présent) en cours d’exécution.|Si total_elapsed_time dépasse la valeur maximale pour un entier (24.8 jours en millisecondes), cela entraînera l’échec de matérialisation en raison d’un dépassement de capacité.<br /><br /> La valeur maximale, en millisecondes est équivalente à 24.8 jours.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
