---
title: MSrepl_errors (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_errors
- MSrepl_errors_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_errors system table
ms.assetid: c6e023c1-2c32-4269-8d76-e442ea309e4b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 70d737e8c73d3e5b6876c2669fbafbc71bea66e0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986467"
---
# <a name="msreplerrors-transact-sql"></a>MSrepl_errors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSrepl_errors** table contient des lignes avec des informations étendues d’échec de l’Agent de Distribution et Agent de fusion. Cette table est stockée dans la base de données de distribution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID de l'erreur.|  
|**time**|**datetime**|Heure de survenue de l'erreur.|  
|**error_type_id**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**source_type_id**|**int**|ID du type de source de l'erreur.|  
|**source_name**|**nvarchar(100)**|Nom de la source de l'erreur.|  
|**error_code**|**sysname**|Code d'erreur.|  
|**error_text**|**ntext**|Message d’erreur.|  
|**xact_seqno**|**varbinary(16)**|Dans le journal des transactions, numéro séquentiel dans le journal de la première transaction du lot dont l'exécution a échoué. Uniquement utilisé par les Agents de distribution, c'est le numéro séquentiel dans le journal de la première transaction dans le lot dont l'exécution a échoué.|  
|**command_id**|**Int**|ID de la commande du lot dont l'exécution a échoué. Utilisé uniquement par les Agents de distribution, il s'agit de l'ID de commande de la première commande du lot en échec.|  
|**session_id**|**int**|ID de la session de l'Agent où l'erreur s'est produite.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
