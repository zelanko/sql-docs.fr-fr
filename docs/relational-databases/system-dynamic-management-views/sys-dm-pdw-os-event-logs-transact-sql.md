---
title: Sys.dm_pdw_os_event_logs (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.reviewer: 
ms.service: 
ms.component: dmv's
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ffd9bad344ed79048a65de4139ec7c2fd44cd9c4
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwoseventlogs-transact-sql"></a>Sys.dm_pdw_os_event_logs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contient des informations concernant les différents événements de Windows les journaux sur des nœuds différents.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Nœud d’équipement que provient ce journal.<br /><br /> pdw_node_id et nom_journal forment la clé pour cette vue.||  
|nom_journal|**nvarchar(255)**|Nom du journal des événements Windows.<br /><br /> pdw_node_id et nom_journal forment la clé pour cette vue.||  
|log_source|**nvarchar(255)**|Nom de source de journal des événements Windows.||  
|event_id|**int**|ID de l’événement. N’est pas unique.||  
|event_type|**nvarchar(255)**|Type de l’événement, en identifiant la gravité.|« Informations », « Avertissement », « Erreur »|  
|event_message|**nvarchar(4000)**|Détails de l’événement.||  
|generate_time|**datetime**|Heure de que création de l’événement.||  
|write_time|**datetime**|Heure de que l’événement a été réellement écrits dans le journal.||  
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez la section valeurs de la vue système Maximum dans la [valeurs minimale et maximale (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9) rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de gestion dynamique de l’entrepôt de données en parallèle &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
