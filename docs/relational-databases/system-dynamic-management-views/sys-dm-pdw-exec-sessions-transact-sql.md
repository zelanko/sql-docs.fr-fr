---
title: sys.dm_pdw_exec_sessions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31c262b3-7e4d-44c4-af71-aaef0fd1a980
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 41042d1dff7a64a8a2d2fe093276f61ab254da56
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56039860"
---
# <a name="sysdmpdwexecsessions-transact-sql"></a>sys.dm_pdw_exec_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les sessions actuellement ou récemment ouvert sur l’appliance. Elle répertorie une ligne par session.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|session_id|**nvarchar(32)**|L’id de la requête actuelle ou la dernière requête exécuter (si la session est ARRÊTÉE et l’exécution de la requête au moment de l’arrêt). Clé pour cette vue.|Unique dans toutes les sessions dans le système.|  
|status|**nvarchar(10)**|Pour les sessions en cours, identifie si la session est actuellement actif ou inactif. Pour des sessions précédentes, la session état peut être fermée ou arrêtée (si la session a dû être fermée).|'ACTIVE', 'CLOSED', 'IDLE', 'TERMINATED'|  
|request_id|**nvarchar(32)**|L’id de la requête actuelle ou de la dernière exécution de la requête.|Unique pour toutes les requêtes dans le système. Null si aucun n’a pas été exécuté.|  
|security_id|**varbinary(85)**|ID de sécurité de l’entité de la session en cours d’exécution.||  
|login_name|**nvarchar(128)**|Le nom de connexion du principal qui exécute la session.|Toute chaîne conforme aux conventions d’affectation de noms utilisateur.|  
|login_time|**datetime**|Date et heure à laquelle l’utilisateur connecté et cette session a été créée.|Valide **datetime** avant l’heure actuelle.|  
|query_count|**Int**|Le nombre de sessions de requêtes/requeststhis a exécuté depuis la création de captures.|Supérieur ou égal à 0.|  
|is_transactional|**bit**|Capture si une session est actuellement dans une transaction ou non.|0 pour la validation automatique, 1 pour transactionnelle.|  
|client_id|**nvarchar(255)**|Capture des informations de client pour la session.|N’importe quelle chaîne valide.|  
|app_name|**nvarchar(255)**|Capture des informations de nom d’application si vous le souhaitez définie en tant que partie du processus de connexion.|N’importe quelle chaîne valide.|  
|sql_spid|**Int**|Numéro d’identification du SPID. Utilisez le `session_id` cette session. Utilisez le `sql_spid` colonne pour joindre au **sys.dm_pdw_nodes_exec_sessions**.<br /><br /> **\*\* Avertissement \* \***  cette colonne contient des SPID fermés.||  
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez la section de valeurs de la vue système maximales dans le [valeurs minimales et maximales (SQL Server PDW)](https://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9) rubrique.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation `VIEW SERVER STATE`.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
