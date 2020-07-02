---
title: sys. dm_fts_fdhosts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_fdhosts
- dm_fts_fdhosts_TSQL
- sys.dm_fts_fdhosts
- sys.dm_fts_fdhosts_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_fdhosts dynamic management view
- troubleshooting [SQL Server], full-text search
ms.assetid: d42a6334-4362-4361-83da-f8324fe55ec7
author: pmasl
ms.author: pelopes
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1b954e5d9c122f09d1ed16162f34ce94cdbc4100
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734572"
---
# <a name="sysdm_fts_fdhosts-transact-sql"></a>sys.dm_fts_fdhosts (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Retourne des informations sur l'activité actuelle de l'hôte ou des hôtes de démon de filtre sur l'instance de serveur.  
  
 
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**fdhost_id**|**int**|ID de l'hôte de démon de filtre.|  
|**fdhost_name**|**nvarchar(120)**|Nom de l'hôte de démon de filtre.|  
|**fdhost_process_id**|**int**|ID de processus Windows de l'hôte de démon de filtre.|  
|**fdhost_type**|**nvarchar(120)**|Type de document traité par l'hôte de démon de filtre, l'un des types suivants :<br /><br /> Thread unique<br /><br /> Multithread<br /><br /> Document énorme|  
|**max_thread**|**int**|Nombre maximal de threads dans l'hôte de démon de filtre.|  
|**batch_count**|**int**|Nombre des lots traités dans l'hôte de démon de filtre.|  
  
## <a name="permissions"></a>Autorisations  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , requiert l' `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   

## <a name="examples"></a>Exemples  
 L'exemple suivant retourne le nom de l'hôte de démon de filtre et le nombre maximal de threads dans cet hôte. Il contrôle également le nombre de lots traités actuellement dans le démon de filtre. Ces informations peuvent être utilisées pour diagnostiquer les performances.  
  
```  
SELECT fdhost_name, batch_count, max_thread FROM sys.dm_fts_fdhosts;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique de la recherche en texte intégral et de la recherche sémantique &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Recherche en texte intégral](../../relational-databases/search/full-text-search.md)  
  
  
