---
title: sys. dm_fts_memory_buffers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_memory_buffers
- dm_fts_memory_buffers_TSQL
- dm_fts_memory_buffers
- sys.dm_fts_memory_buffers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_buffers dynamic management view
ms.assetid: 56895fe5-e8df-4d75-9adc-c1f7757cdef8
author: pmasl
ms.author: pelopes
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fed15fbcfa685bde5d408e799bb605a40380ab5a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265922"
---
# <a name="sysdm_fts_memory_buffers-transact-sql"></a>sys.dm_fts_memory_buffers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les zones de mémoire tampon appartenant à un pool de mémoire spécifique et utilisées dans le cadre d'une analyse de texte intégral ou d'une plage d'analyses de texte intégral.  
  
> [!NOTE]
> La colonne suivante sera supprimée dans une version ultérieure de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **row_count**. Évitez d'employer cette colonne pour de nouvelles tâches de développement et pensez éventuellement à modifier les applications qui l'utilisent actuellement.  

  
|Colonne|Type de données|Description|  
|------------|---------------|-----------------|  
|**pool_id**|**int**|ID du pool de mémoire alloué.<br /><br /> 0 = petites zones de mémoire tampon<br /><br /> 1 = grandes zones de mémoire tampon|  
|**memory_address**|**varbinary (8)**|Adresse de la zone de mémoire tampon allouée.|  
|**nomme**|**nvarchar(4000)**|Nom de la zone de mémoire tampon partagée pour laquelle cette allocation a été effectuée.|  
|**is_free**|**bit**|État actuel de la zone de mémoire tampon.<br /><br /> 0 = libre<br /><br /> 1 = occupé|  
|**row_count**|**int**|Nombre de lignes que gère actuellement cette zone de mémoire tampon.|  
|**bytes_used**|**int**|Quantité, en octets, de mémoire utilisée dans cette zone de mémoire tampon.|  
|**percent_used**|**int**|Pourcentage de mémoire allouée utilisé.|  
  
## <a name="permissions"></a>Autorisations  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` l’autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   
  
## <a name="physical-joins"></a>Jointures physiques  
 ![Jointures significatives de cette vue de gestion dynamique](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-buffers-1.gif "Jointures significatives de cette vue de gestion dynamique")  
  
## <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|De|À|Relation|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Fonctions et vues de gestion dynamique de la recherche en texte intégral et de la recherche sémantique &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

