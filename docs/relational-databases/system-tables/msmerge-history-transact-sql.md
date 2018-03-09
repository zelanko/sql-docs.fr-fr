---
title: MSmerge_history (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- MSmerge_history_TSQL
- MSmerge_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_history system table
ms.assetid: 936195ad-ca07-41a8-a1a0-6699b6e63403
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bec33dfc63fb25943be93ff79c2a15136473c06a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="msmergehistory-transact-sql"></a>MSmerge_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_history** table contient des lignes d’historique avec une description détaillée des résultats des sessions précédentes du travail de l’Agent de fusion. Cette table contient une ligne par ligne de sortie de l'Agent. Cette table est utilisée dans la base de données de distribution et dans chaque base de données d'abonnement. Dans la base de données de distribution, elle contient l'historique de toutes les publications de fusion et de tous les abonnements de fusion qui utilisent le serveur de distribution. Dans chaque base de données d'abonnement, il contient l'historique des publications auxquelles l'Abonné a souscrit.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|ID du travail d'Agent de fusion|  
|**éléments agent_id**|**int**|ID de l'Agent de fusion|  
|**commentaires**|**nvarchar(255)**|Texte du message.|  
|**ID_erreur**|**int**|L’ID d’une erreur dans le [MSrepl_errors](../../relational-databases/system-tables/msrepl-errors-transact-sql.md) (table système).|  
|**timestamp**|**timestamp**|Colonne timestamp de cette table|  
|**updatable_row**|**bit**|La valeur **1** si la ligne d’historique peut être remplacée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
