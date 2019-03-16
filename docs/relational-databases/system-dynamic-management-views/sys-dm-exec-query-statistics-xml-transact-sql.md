---
title: sys.dm_exec_query_statistics_xml (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_statistics_xml
- sys.dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml
helpviewer_keywords:
- sys.dm_exec_query_statistics_xml management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfecb
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 63e1d22670929448110083c31e9900e462d576bc
ms.sourcegitcommit: 671370ec2d49ed0159a418b9c9ac56acf43249ad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072303"
---
# <a name="sysdmexecquerystatisticsxml-transact-sql"></a>sys.dm_exec_query_statistics_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Retourne plan de requête d’exécution pour les demandes en cours. Utilisez cette vue de gestion dynamique pour récupérer de showplan XML avec des statistiques temporaires. 

## <a name="syntax"></a>Syntaxe

```
sys.dm_exec_query_statistics_xml(session_id)  
``` 

## <a name="arguments"></a>Arguments 
*session_id*  
 L’id de session exécute le lot à rechercher. *session_id* est **smallint**. *session_id* peut être obtenu à partir d’objets de gestion dynamique suivants :  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  

## <a name="table-returned"></a>Table retournée

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|
|session_id|**smallint**|ID de la session. N'accepte pas la valeur NULL.|
|request_id|**Int**|ID de la demande. N'accepte pas la valeur NULL.|
|sql_handle|**varbinary(64)**|Table de hachage du texte SQL de la demande. Autorise la valeur Null.|
|plan_handle|**varbinary(64)**|Table de hachage du plan de requête. Autorise la valeur Null.|
|query_plan|**xml**|Showplan XML avec des statistiques partielles. Autorise la valeur Null.|

## <a name="remarks"></a>Notes
Cette fonction système est disponible à partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1. Consultez la base de connaissances [3190871](https://support.microsoft.com/en-us/help/3190871)

Cette fonction système fonctionne dans les répertoires **standard** et **léger** infrastructure de profilage des statistiques d’exécution de requête. Pour plus d’informations, consultez [Infrastructure du profilage de requête](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md).  

## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation `VIEW SERVER STATE` sur le serveur.  

## <a name="examples"></a>Exemples  
  
### <a name="a-looking-at-live-query-plan-and-execution-statistics-for-a-running-batch"></a>A. Examinez les statistiques de plan et l’exécution des requêtes actives pour un lot en cours d’exécution  
 L’exemple suivant interroge **sys.dm_exec_requests** pour rechercher la requête vous intéresse et copie son `session_id` à partir de la sortie.  
  
```sql  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 Ensuite, pour obtenir les statistiques de plan et l’exécution de requêtes actives, utilisez le texte copié `session_id` avec la fonction système **sys.dm_exec_query_statistics_xml**.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_query_statistics_xml(< copied session_id >);  
GO  
```   

 Ou combiné pour toutes les demandes en cours d’exécution.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_requests
CROSS APPLY sys.dm_exec_query_statistics_xml(session_id);  
GO  
```   
  
## <a name="see-also"></a>Voir aussi
  [Indicateurs de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à la base de données &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

