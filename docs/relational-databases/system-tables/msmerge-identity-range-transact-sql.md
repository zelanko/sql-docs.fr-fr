---
title: MSmerge_identity_range (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_TSQL
- MSmerge_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range system table
ms.assetid: 493a2028-88a0-4e83-ad89-ae5661d9f477
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 672715bb7bfa83767975c399f75595af04f23d57
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825818"
---
# <a name="msmerge_identity_range-transact-sql"></a>MSmerge_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSmerge_identity_range** permet d’effectuer le suivi des plages numériques affectées aux colonnes d’identité pour l’abonnement aux publications sur lesquelles la réplication gère automatiquement ces affectations de plage. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|Numéro d'identification unique d'un abonnement donné.|  
|**artid**|**uniqueidentifier**|Numéro d'identification unique de l'article donné.|  
|**range_begin**|**numérique (38)**|Valeur d'identité au début de la plage actuelle.|  
|**range_end**|**numérique (38)**|Valeur d'identité à la fin de la plage actuelle.|  
|**next_range_begin**|**numérique (38)**|Valeur d'identité au début de la plage suivante à affecter.|  
|**next_range_end**|**numérique (38)**|Valeur d'identité à la fin de la plage suivante à affecter.|  
|**is_pub_range**|**bit**|La valeur **1** si la plage d’identité est assignée à la publication.|  
|**max_used**|**numérique (38)**|Valeur d'identité maximale pouvant être affectée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
