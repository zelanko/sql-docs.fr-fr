---
title: MSsync_states (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- MSsync_states
- MSsync_states_TSQL
dev_langs: TSQL
helpviewer_keywords: MSsync_states system table
ms.assetid: b25e17e1-7718-432e-a442-c4946741d474
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1ba8b39693791917df675e80fcaff8ffb51a0c2a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssyncstates-transact-sql"></a>MSsync_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSsync_states** quelle publication se trouve toujours en mode de capture instantanée de la table. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|L’ID du serveur de publication.|  
|**publisher_db**|**sysname**|Le nom de la base de données de publication.|  
|**id_de_la_publication**|**int**|ID de la publication.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Les Services d’intégration des Tables &#40; Transact-SQL &#41;](../../relational-databases/system-tables/integration-services-tables-transact-sql.md)   
 [Sauvegarde et restauration Tables &#40; Transact-SQL &#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [Tables de copie des journaux de transaction &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)  
  
  
