---
title: MSreplication_queue (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_queue
- MSreplication_queue_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_queue system table
ms.assetid: 664bf817-8021-4417-96d6-2bb1e4baabff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3bdbfed403a8b85a195134e053a151905efa128f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889426"
---
# <a name="msreplication_queue-transact-sql"></a>MSreplication_queue (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La table **MSreplication_queue** est utilisée par le processus de réplication pour stocker les commandes mises en file d’attente émises par tous les abonnements de mise à jour en attente qui utilisent des mises en file d’attente SQL. Cette table est stockée dans la base de données d’abonnement.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nom du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données de publication.|  
|**édition**|**sysname**|Nom de la publication.|  
|**tranid**|**sysname**|Identificateur de transaction sous lequel la commande en file d'attente a été exécutée.|  
|**data**|**varbinary(8000)**|Flux d'octets empaqueté où étaient stockées les informations sur la commande mise en file d'attente.|  
|**datalen**|**int**|Longueur des données en octets.|  
|**CommandType**|**int**|Type de commande mise en file d'attente :<br /><br /> 1 = Commande utilisateur dans une transaction<br /><br /> 2 = Commande de synchronisation d'abonnement|  
|**insertdate**|**datetime**|Date d'insertion.|  
|**orderkey**|**bigint**|Colonne d'identité à croissance monolithique.|  
|**cmdstate**|**bit**|État de la commande :<br /><br /> 0 = Terminée<br /><br /> 1 = Partiellement exécutée|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
