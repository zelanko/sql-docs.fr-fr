---
title: MSreplication_queue (Transact-SQL) | Documents Microsoft
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
- MSreplication_queue
- MSreplication_queue_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_queue system table
ms.assetid: 664bf817-8021-4417-96d6-2bb1e4baabff
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 25bbbc37215010d60cd20a01ea06cb35176eabf5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="msreplicationqueue-transact-sql"></a>MSreplication_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSreplication_queue** table est utilisée par le processus de réplication pour stocker les commandes en file d’attente émises par les en file d’attente les abonnements de mise à jour en file d’attente qui sont à l’aide de basé sur SQL. Cette table est stockée dans la base de données d’abonnement.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**publisher** (serveur de publication)|**sysname**|Le nom du serveur de publication.|  
|**publisher_db**|**sysname**|Le nom de la base de données de publication.|  
|**publication**|**sysname**|Nom de la publication.|  
|**tranid**|**sysname**|Identificateur de transaction sous lequel la commande en file d'attente a été exécutée.|  
|**données**|**varbinary (8000)**|Flux d'octets empaqueté où étaient stockées les informations sur la commande mise en file d'attente.|  
|**datalen**|**int**|Longueur des données en octets.|  
|**CommandType**|**int**|Type de commande mise en file d'attente :<br /><br /> 1 = Commande utilisateur dans une transaction<br /><br /> 2 = Commande de synchronisation d'abonnement|  
|**insertdate**|**datetime**|Date d'insertion.|  
|**orderkey**|**bigint**|Colonne d'identité à croissance monolithique.|  
|**cmdstate**|**bit**|État de la commande :<br /><br /> 0 = Terminée<br /><br /> 1 = Partiellement exécutée|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
