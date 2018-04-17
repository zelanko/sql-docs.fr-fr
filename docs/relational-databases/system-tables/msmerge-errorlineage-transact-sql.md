---
title: MSmerge_errorlineage (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- MSmerge_errorlineage_TSQL
- MSmerge_errorlineage
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_errorlineage system table
ms.assetid: 3bcbd328-c958-4cd4-a573-3c35539fa919
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c11b1f3f9da7d6fedd4521cec0a1620f87f8b4f8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="msmergeerrorlineage-transact-sql"></a>MSmerge_errorlineage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_errorlineage** table contient des lignes qui ont été supprimées sur l’abonné, mais dont la suppression n’est pas propagée vers le serveur de publication. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Valeur d'entier affectée à la table publiée pour la réplication de fusion. Correspond au champ de surnom dans le **sysmergearticles** table.|  
|**ROWGUID**|**uniqueidentifier**|Identificateur de ligne.|  
|**lignage**|**Varbinary(501)**|Stocke une liste historique à partir de laquelle les Abonnés et les serveurs de publication ont apporté des mises à jour sur une ligne. Utilisé pour détecter et résoudre des situations conflictuelles.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
