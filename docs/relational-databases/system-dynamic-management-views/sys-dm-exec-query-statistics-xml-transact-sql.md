---
title: Sys.dm_exec_query_statistics_xml (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: 99e51be32264dd90b126860b33abe35c7a27781a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52819101"
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

Cette fonction système fonctionne dans les répertoires **standard** et **léger** infrastructure de profilage des statistiques d’exécution de requête.  
  
**Standard** infrastructure de profilage des statistiques peuvent être activées à l’aide de :
  -  [SET STATISTICS XML SUR](../../t-sql/statements/set-statistics-xml-transact-sql.md)
  -  [SET STATISTICS PROFILE SUR](../../t-sql/statements/set-statistics-profile-transact-sql.md)
  -  le `query_post_execution_showplan` événements étendus.  
  
**Lightweight** infrastructure de profilage des statistiques est disponible dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 et peuvent être activées :
  -  Dans le monde entier à l’aide de trace indicateur 7412.
  -  À l’aide de la [ *query_thread_profile* ](https://support.microsoft.com/kb/3170113) événements étendus.
  
> [!NOTE]
> Une fois activé par l’indicateur de trace 7412, profilage léger être activé à tout consommateur des statistiques d’exécution de requête infrastructure au lieu de Profiler standard, telles que la vue de gestion dynamique de profilage [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md).
> Toutefois, le profilage standard est toujours utilisé pour SET STATISTICS XML, *inclure le Plan réel* action dans [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)], et `query_post_execution_showplan` xEvent.

> [!IMPORTANT]
> Dans TPC-C comme tests de charge de travail, l’activation de l’infrastructure de profilage légère de statistiques ajoute une surcharge de 1,5 à 2 %. En revanche, l’infrastructure de profilage de statistiques standard peut ajouter jusqu'à 90 % de surcharge pour le même scénario de charge de travail.

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

