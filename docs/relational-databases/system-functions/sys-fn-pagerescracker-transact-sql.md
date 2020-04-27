---
title: sys. fn_PageResCracker (Transact-SQL) | Microsoft Docs
description: Documentation relative à la fonction système sys. fn_PageResCracker.
ms.custom: ''
ms.date: 09/18/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_PageResCracker
- sys.fn_PageResCracker_TSQL
- fn_PageResCracker_TSQL
- sys.fn_PageResCracker
- sys.dm_db_page_info
dev_langs:
- TSQL
helpviewer_keywords:
- fn_PageResCracker function
- page_resource
- sys.fn_PageResCracker function
- sys.dm_db_page_info
- page info
author: bluefooted
ms.author: pamela
manager: amitban
ms.openlocfilehash: 6d8203979a0afdca1ae78b9bd51723c906c40ea2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68267072"
---
# <a name="sysfn_pagerescracker-transact-sql"></a>sys. fn_PageResCracker (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Retourne `db_id`, `file_id`et `page_id` pour la valeur donnée. `page_resource` 
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
```  
sys.fn_PageResCracker ( page_resource )  
```  
  
## <a name="arguments"></a>Arguments  
*page_resource*    
Format hexadécimal sur 8 octets d’une ressource de page de base de données.
  
## <a name="tables-returned"></a>Tables retournées  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|db_id|**int**|ID de base de données|  
|file_id|**int**|ID de fichier|  
|page_id|**int**|ID de page|  
  
## <a name="remarks"></a>Notes  
`sys.fn_PageResCracker`est utilisé pour convertir la représentation hexadécimale sur 8 octets d’une page de base de données en un ensemble de lignes qui contient l’ID de base de données, l’ID de fichier et l’ID de page de la page.   

Vous pouvez obtenir une ressource de page valide à `page_resource` partir de la colonne de la vue de gestion dynamique [sys. dm_exec_requests &#40;transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) ou de la vue système [sys. sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md) . Si une ressource de page non valide est utilisée, le retour est NULL.  
L’utilisation principale de `sys.fn_PageResCracker` est de faciliter les jointures entre ces vues et la fonction [sys. dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) la fonction de gestion dynamique pour obtenir des informations sur la page, telles que l’objet auquel elle appartient.
  
## <a name="permissions"></a>Autorisations  
L’utilisateur a `VIEW SERVER STATE` besoin d’une autorisation sur le serveur.  
  
## <a name="examples"></a>Exemples  
La `sys.fn_PageResCracker` fonction peut être utilisée conjointement avec [sys. dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) pour résoudre les attentes et les blocages liés aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]pages dans.  Le script suivant est un exemple de la façon dont vous pouvez utiliser ces fonctions pour collecter des informations de page de base de données pour toutes les demandes actives qui attendent actuellement un type de ressource de page. 
  
```sql  
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 1) AS page_info
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys. dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)  
 [sys. sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  
