---
title: MSpublicationthresholds (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- mspublicationthresholds
- mspublicationthresholds_TSQL
dev_langs: TSQL
helpviewer_keywords: MSpublicationthresholds system table
ms.assetid: 9da3879f-b1f4-4ab4-abd4-a9a8ac395eba
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c485a00706ab9620bb944ae2843c4f9ba96e75b2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mspublicationthresholds-transact-sql"></a>MSpublicationthresholds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSpublicationthresholds** table est utilisée pour effectuer le suivi des mesures de performances de réplication pour une publication, avec une ligne pour chaque valeur de seuil en cours d’analyse. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**id_de_la_publication**|**int**|Identifie la publication pour laquelle un seuil a été défini.|  
|**metric_id**|**int**|Identifie une mesure de performances de réplication surveillée telle que définie dans le [MSreplmonthresholdmetrics](../../relational-databases/system-tables/msreplmonthresholdmetrics-transact-sql.md) (table système).|  
|**valeur**|**sql_variant**|Valeur de seuil de la mesure surveillée.|  
|**shouldalert**|**bit**|La valeur **1** indique qu’une alerte doit être générée lorsque la mesure dépasse le seuil défini.|  
|**IsEnabled**|**bit**|La valeur **1** indique que la surveillance est activée pour cette métrique de performance de réplication.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
