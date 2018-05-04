---
title: Sys.dm_pdw_exec_connections (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8f55c2f5b98aa1778c8772dc30fffd16fe522ca7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmpdwexecconnections-transact-sql"></a>Sys.dm_pdw_exec_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Retourne des informations sur les connexions établies à cette instance de [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et les détails de chaque connexion.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|session_id|**int**|Identifie la session associée à cette connexion. Utilisez `SESSION_ID()` pour renvoyer le `session_id` de la connexion actuelle.|  
|connect_time|**datetime**|Cachet temporel d'établissement de la connexion. N'accepte pas la valeur NULL.|  
|encrypt_option|**nvarchar(40)**|Indique la valeur TRUE (la connexion est chiffrée) ou la valeur FALSE (la connexion n’est pas enctypred).|  
|auth_scheme|**nvarchar(40)**|Spécifie le schéma d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Windows utilisé avec cette connexion. N'accepte pas la valeur NULL.|  
|client_id|**varchar(48)**|Adresse IP du client se connectant à ce serveur. Autorise la valeur NULL.|  
|sql_spid|**int**|L’ID de processus serveur, de la connexion. Utilisez `@@SPID` pour renvoyer le `sql_spid` de la connexion actuelle. Pour plus de dédié, utilisez le `session_id` à la place.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert **VIEW SERVER STATE** autorisation sur le serveur.  
  
## <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
||||  
|-|-|-|  
|dm_pdw_exec_sessions.session_id|dm_pdw_exec_connections.session_id|Un à un|  
|dm_pdw_exec_requests.connection_id|dm_pdw_exec_connections.connection_id|Plusieurs-à-un|  
  
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
 [Entrepôt de données SQL et les données en parallèle de l’entrepôt de vues de gestion dynamique &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

