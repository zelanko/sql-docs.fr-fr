---
title: MSrepl_queuedtraninfo (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSrepl_queuedtraninfo_TSQL
- MSrepl_queuedtraninfo
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_queuedtraninfo system table
ms.assetid: af7a5baf-32ea-475f-b6b9-68c557b4980c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5d7caf6825e7bcb3f17f4824b07ca931ee083998
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="msreplqueuedtraninfo-transact-sql"></a>MSrepl_queuedtraninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSreplication_queuedtraninfo** table est utilisée par le processus de réplication pour stocker des informations sur les commandes en file d’attente émises par tous les abonnements mis à jour en file d’attente qui utilisent la mise à jour en file d’attente basé sur SQL. Cette table est stockée dans la base de données d’abonnement.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**publisher** (serveur de publication)|**sysname**|Le nom du serveur de publication.|  
|**publisher_db**|**sysname**|Le nom de la base de données de publication.|  
|**publication**|**sysname**|Nom de la publication.|  
|**tranid**|**sysname**|Identificateur de transaction sous lequel la commande en file d'attente a été exécutée.|  
|**maxorderkey**|**bigint**|Interne-usage.|  
|**commandcount**|**bigint**|Interne-usage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
