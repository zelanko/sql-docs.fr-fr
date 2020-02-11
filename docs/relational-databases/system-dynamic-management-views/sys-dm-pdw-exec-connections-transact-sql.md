---
title: sys. dm_pdw_exec_connections (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b333af29e3d39c0f4ce59ea68602f652c042003f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899416"
---
# <a name="sysdm_pdw_exec_connections-transact-sql"></a>sys. dm_pdw_exec_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Retourne des informations sur les connexions établies à cette instance de [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et les détails de chaque connexion.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|session_id|**int**|Identifie la session associée à cette connexion. Utilisez `SESSION_ID()` pour retourner le `session_id` de la connexion actuelle.|  
|connect_time|**DATETIME**|Cachet temporel d'établissement de la connexion. N'accepte pas la valeur NULL.|  
|encrypt_option|**nvarchar (40)**|Indique la valeur TRUE (la connexion est chiffrée) ou FALSe (la connexion n’est pas enctypred).|  
|auth_scheme|**nvarchar (40)**|Spécifie le schéma d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Windows utilisé avec cette connexion. N'accepte pas la valeur NULL.|  
|client_id|**varchar (48)**|Adresse IP du client qui se connecte à ce serveur. Autorise la valeur NULL.|  
|sql_spid|**int**|ID de processus serveur de la connexion. Utilisez `@@SPID` pour retourner le `sql_spid` de la connexion actuelle. Pour la plupart des cas, utilisez `session_id` à la place.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation **View Server State** sur le serveur.  
  
## <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
||||  
|-|-|-|  
|dm_pdw_exec_sessions. session_id|dm_pdw_exec_connections. session_id|Un-à-un|  
|dm_pdw_exec_requests. connection_id|dm_pdw_exec_connections. connection_id|Plusieurs-à-un|  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Requête typique pour collecter des informations sur une connexion propre aux requêtes.  
  
```  
SELECT  
    c.session_id, c.encrypt_option,  
    c.auth_scheme, s.client_id, s.login_name,   
    s.status, s.query_count  
FROM sys.dm_pdw_exec_connections AS c  
JOIN sys.dm_pdw_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = SESSION_ID();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

