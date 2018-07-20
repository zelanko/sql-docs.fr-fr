---
title: MSreplication_queue (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
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
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 663a07279a7bfe0ba9afe8ce6dc37cd74c71434c
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102137"
---
# <a name="msreplicationqueue-transact-sql"></a>MSreplication_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSreplication_queue** table est utilisée par le processus de réplication pour stocker les commandes en file d’attente émises par les en file d’attente les abonnements mis à jour en file d’attente qui sont à l’aide de basé sur SQL. Cette table est stockée dans la base de données d’abonnement.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher** (serveur de publication)|**sysname**|Le nom du serveur de publication.|  
|**publisher_db**|**sysname**|Le nom de la base de données de publication.|  
|**publication**|**sysname**|Nom de la publication.|  
|**tranid**|**sysname**|Identificateur de transaction sous lequel la commande en file d'attente a été exécutée.|  
|**data**|**varbinary(8000)**|Flux d'octets empaqueté où étaient stockées les informations sur la commande mise en file d'attente.|  
|**datalen**|**Int**|Longueur des données en octets.|  
|**CommandType**|**Int**|Type de commande mise en file d'attente :<br /><br /> 1 = Commande utilisateur dans une transaction<br /><br /> 2 = Commande de synchronisation d'abonnement|  
|**insertdate**|**datetime**|Date d'insertion.|  
|**orderkey**|**bigint**|Colonne d'identité à croissance monolithique.|  
|**cmdstate**|**bit**|État de la commande :<br /><br /> 0 = Terminée<br /><br /> 1 = Partiellement exécutée|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
