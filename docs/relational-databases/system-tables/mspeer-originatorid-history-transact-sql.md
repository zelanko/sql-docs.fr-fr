---
title: MSpeer_originatorid_history (Transact-SQL) | Documents Microsoft
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
- MSpeer_originatorid_history_TSQL
- MSpeer_originatorid_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_originatorid_history
ms.assetid: c1f53d0f-4080-43ff-be38-2b10395c68c9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5c98612ad170d6b8490b222defa60a5cdc46672b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mspeeroriginatoridhistory-transact-sql"></a>MSpeer_originatorid_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque ID d'appelant défini dans la topologie. Ces informations incluent les ID des nœuds qui ne sont plus actifs. La table est utilisée lorsque vous configurez un nouveau nœud pour la détection de conflit afin de garantir que l'ID d'appelant spécifié n'a pas déjà été utilisé. Cette table est stockée dans la base de données de publication. Pour plus d’informations sur la détection de conflit, consultez [la détection de conflit dans la réplication d’égal à égal](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|originator_publication|**sysname**|Publication pour laquelle l'ID d'appelant a été spécifié.|  
|originator_id|**int**|Nombre qui identifie chaque nœud dans la topologie à des fins de détection de conflit|  
|originator_node|**sysname**|Instance de serveur pour laquelle l'ID d'appelant a été spécifié.|  
|originator_db|**sysname**|Base de données de publication pour laquelle l'ID d'appelant a été spécifié.|  
|originator_db_version|**int**|Identifie le numéro de version de la base de données d'origine.|  
|originator_version|**int**|Spécifie le numéro de version du serveur de publication.|  
|inserted_date|**datetime**|Date et heure d'insertion de la ligne de l'ID d'appelant dans cette table.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
