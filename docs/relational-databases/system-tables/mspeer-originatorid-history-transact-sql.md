---
title: MSpeer_originatorid_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_originatorid_history_TSQL
- MSpeer_originatorid_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_originatorid_history
ms.assetid: c1f53d0f-4080-43ff-be38-2b10395c68c9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3dff36fb672d7d94d9716f0c8eaefbb6132f9536
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52810501"
---
# <a name="mspeeroriginatoridhistory-transact-sql"></a>MSpeer_originatorid_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque ID d'appelant défini dans la topologie. Ces informations incluent les ID des nœuds qui ne sont plus actifs. La table est utilisée lorsque vous configurez un nouveau nœud pour la détection de conflit afin de garantir que l'ID d'appelant spécifié n'a pas déjà été utilisé. Cette table est stockée dans la base de données de publication. Pour plus d’informations sur la détection de conflit, consultez [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|originator_publication|**sysname**|Publication pour laquelle l'ID d'appelant a été spécifié.|  
|originator_id|**Int**|Nombre qui identifie chaque nœud dans la topologie à des fins de détection de conflit|  
|originator_node|**sysname**|Instance de serveur pour laquelle l'ID d'appelant a été spécifié.|  
|originator_db|**sysname**|Base de données de publication pour laquelle l'ID d'appelant a été spécifié.|  
|originator_db_version|**Int**|Identifie le numéro de version de la base de données d'origine.|  
|originator_version|**Int**|Spécifie le numéro de version du serveur de publication.|  
|inserted_date|**datetime**|Date et heure d'insertion de la ligne de l'ID d'appelant dans cette table.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
