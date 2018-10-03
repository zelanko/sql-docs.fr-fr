---
title: MSreplication_subscriptions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSreplication_subscriptions
- MSreplication_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_subscriptions system table
ms.assetid: fd0c5843-4e9b-4448-8bfb-0a4067d1d8d1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f195247e3daf764903028e8ba10ca0d7dd24a426
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800837"
---
# <a name="msreplicationsubscriptions-transact-sql"></a>MSreplication_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSreplication_subscriptions** table contient une ligne d’informations de réplication pour chaque Agent de Distribution de la base de données d’abonné locale. Cette table est stockée dans la base de données d’abonnement.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher** (serveur de publication)|**sysname**|Le nom du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données du serveur de publication.|  
|**publication**|**sysname**|Nom de la publication.|  
|**independent_agent**|**bit**|Indique s'il existe un Agent de distribution autonome pour cette publication.|  
|**subscription_type**|**Int**|Le type d’abonnement :<br /><br /> 0 = Par envoi de données (push).<br /><br /> 1 = Par extraction de données (pull).<br /><br /> 2 = Anonyme.|  
|**distribution_agent**|**sysname**|Nom de l'Agent de distribution.|  
|**Time**|**smalldatetime**|Heure de la dernière mise à jour effectuée par l'Agent de distribution.|  
|**description**|**nvarchar(255)**|Description de l'abonnement.|  
|**transaction_timestamp**|**varbinary(16)**|Interne-usage uniquement.|  
|**update_mode**|**tinyint**|Type de mise à jour.|  
|**agent_id**|**binary (16)**|ID de l'Agent.|  
|**subscription_guid**|**binary (16)**|Identificateur global de la version de l'abonnement sur la publication.|  
|**subid**|**binary (16)**|Identificateur global d'un abonnement anonyme.|  
|**immediate_sync**|**bit**|Indique si des fichiers de synchronisation sont créés ou recréés lors de chaque exécution de l'Agent d'instantané.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
