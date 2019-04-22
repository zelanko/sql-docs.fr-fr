---
title: sys.fn_PageResCracker (Transact-SQL) | Microsoft Docs
description: Documentation de la fonction de système de sys.fn_PageResCracker.
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
ms.openlocfilehash: 2fc7136b60dba47813b9942316ee6fdfbc64f307
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58899705"
---
# <a name="sysfnpagerescracker-transact-sql"></a>sys.fn_PageResCracker (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Retourne le `db_id`, `file_id`, et `page_id` pour la donnée `page_resource` valeur. 
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
```  
sys.fn_PageResCracker ( page_resource )  
```  
  
## <a name="arguments"></a>Arguments  
*page_resource*    
Est le format hexadécimal de 8 octets d’une ressource de page de base de données.
  
## <a name="tables-returned"></a>Tables retournées  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|db_id|**Int**|ID de la base de données|  
|file_id|**Int**|ID de fichier|  
|page_id|**Int**|ID de page|  
  
## <a name="remarks"></a>Notes  
`sys.fn_PageResCracker` permet de convertir la représentation hexadécimale sur 8 octets d’une page de base de données à un ensemble de lignes qui contient l’ID de base de données, fichier ID et l’ID de page de la page.   

Vous pouvez obtenir une ressource de page valide à partir de la `page_resource` colonne de la [sys.dm_exec_requests &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) vue de gestion dynamique ou le [sys.sysprocesses &#40;&#41; ](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md) vue système. Si une ressource de page non valide est utilisée la valeur de retour est NULL.  
La principale utilisation de `sys.fn_PageResCracker` est de faciliter les jointures entre ces vues et les [sys.dm_db_page_info &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) fonction de gestion dynamique afin d’obtenir des informations sur la page, comme le objet auquel il appartient.
  
## <a name="permissions"></a>Autorisations  
L’utilisateur doit avoir `VIEW SERVER STATE` autorisation sur le serveur.  
  
## <a name="examples"></a>Exemples  
Le `sys.fn_PageResCracker` fonction peut être utilisée conjointement avec [sys.dm_db_page_info &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) pour résoudre les problèmes de page liés attentes et blocage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Le script suivant est un exemple de comment vous pouvez utiliser ces fonctions pour recueillir des informations de page de base de données pour toutes les demandes actives qui sont actuellement en attente sur un type de ressource de page. 
  
```sql  
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 1) AS page_info
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)  
 [sys.sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  
