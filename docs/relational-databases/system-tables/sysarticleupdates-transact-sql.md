---
title: sysarticleupdates (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticleupdates_TSQL
- sysarticleupdates
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticleupdates system table
ms.assetid: 11a53bcd-a215-4d0b-9db8-233981d3ef5d
author: stevestein
ms.author: sstein
ms.openlocfilehash: d2e710bdbe8f026624ea71357afb6d204b333c91
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68130497"
---
# <a name="sysarticleupdates-transact-sql"></a>sysarticleupdates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque article prenant en charge les abonnements acceptant les mises à jour immédiates. Cette table est stockée dans la base de données répliquée.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Colonne d'identité fournissant un numéro d'identification unique à l'article|  
|**pubid**|**int**|Identificateur de la publication à laquelle appartient l'article|  
|**sync_ins_proc**|**int**|ID de la procédure stockée gérant les transactions d'insertion synchrone|  
|**sync_upd_proc**|**int**|ID de la procédure stockée gérant les transactions de mise à jour synchrone|  
|**sync_del_proc**|**int**|ID de la procédure stockée gérant les transactions de suppression synchrone|  
|**autogen**|**bit**|Signale que les procédures stockées sont générées automatiquement :<br /><br /> **0** = false, non automatique.<br /><br /> **1** = true, automatique.|  
|**sync_upd_trig**|**int**|ID du déclencheur d'application automatique de numéro de version pour la table de l'article|  
|**conflict_tableid**|**Int**|ID de la table de conflits|  
|**ins_conflict_proc**|**Int**|L’ID de la procédure utilisée pour écrire le conflit à le **conflict_table**.|  
|**identity_support**|**bit**|Indique si la gestion automatique des plages d'identités est activée lorsque la mise à jour en attente est utilisée. **0** signifie qu’il n’existe aucune identité de la plage prise en charge.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
