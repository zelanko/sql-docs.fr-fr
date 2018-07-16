---
title: Sys.dm_pdw_exec_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 966fbd2efde6934f8cfe1b59706dec27b92e301e
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926140"
---
# <a name="sysdmpdwexecrequests-transact-sql"></a>Sys.dm_pdw_exec_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les demandes actuellement ou récemment active dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Elle répertorie une ligne par/requête de la demande.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Clé pour cette vue. Id numérique unique associé à la demande.|Unique pour toutes les requêtes dans le système.|  
|session_id|**nvarchar(32)**|Id numérique unique associé à la session dans laquelle cette requête a été exécutée. Consultez [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|État actuel de la demande.|« Running », « Suspendue », « Terminée », « Annulé », « Échec ».|  
|submit_time|**datetime**|Heure à laquelle la demande a été soumise pour exécution.|Valide **datetime** inférieure ou égale à l’heure actuelle et start_time.|  
|start_time|**datetime**|Heure de début de l’exécution de la demande.|NULL pour les demandes en file d’attente ; Sinon, valide **datetime** inférieure ou égale à l’heure actuelle.|  
|end_compile_time|**datetime**|Heure à laquelle le moteur a terminé la compilation de la demande.|NULL pour les requêtes qui n’ont pas été compilés encore ; sinon valide **datetime** start_time inférieure et inférieure ou égale à l’heure actuelle.|
|end_time|**datetime**|Heure à laquelle l’exécution de la requête terminée, a échoué ou a été annulée.|NULL pour les demandes en file d’attente ou actives ; Sinon, valide **datetime** inférieure ou égale à l’heure actuelle.|  
|total_elapsed_time|**Int**|Temps écoulé dans l’exécution dans la mesure où la demande a été démarrée, en millisecondes.|Comprise entre 0 et la différence entre start_time et end_time.<br /><br /> Si total_elapsed_time dépasse la valeur maximale d’un entier, total_elapsed_time continueront à être la valeur maximale. Cette condition génère l’avertissement « la valeur maximale a été dépassée. »<br /><br /> La valeur maximale en millisecondes est équivalente à 24,8 jours environ.|  
|étiquette|**nvarchar(255)**|Chaîne d’étiquette facultative associée à des instructions de la requête SELECT.|Toute chaîne contenant 'a-z', 'A-Z','0-9', '_'.|  
|error_id|**nvarchar(36)**|Id unique de l’erreur associée à la demande, le cas échéant.|Consultez [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); la valeur NULL si aucune erreur ne s’est produite.|  
|database_id|**Int**|Identificateur de la base de données utilisée par le contexte explicite (par exemple, utilisez DB_X).|Consultez les id dans [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|commande|**nvarchar(4000)**|Contient le texte intégral de la demande et soumis par l’utilisateur.|Tout texte de requête ou de requête valid. Requêtes qui comptent plus de 4 000 octets sont tronquées.|  
|resource_class|**nvarchar(20)**|La classe de ressources pour cette demande. Consultez lié **concurrency_slots_used** dans [sys.dm_pdw_resource_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md).|SmallRC<br /><br /> MediumRC<br /><br /> LargeRC<br /><br /> XLargeRC|  
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez « Minimum et valeurs maximales » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation VIEW SERVER STATE.  
  
## <a name="security"></a>Sécurité  
 Sys.dm_pdw_exec_requests ne filtre pas les résultats de la requête en fonction des autorisations spécifiques à la base de données. Connexions avec l’autorisation VIEW SERVER STATE peuvent obtenir des résultats les résultats de requête pour toutes les bases de données  
  
> [!WARNING]  
>  Une personne malveillante peut utiliser sys.dm_pdw_exec_requests pour récupérer des informations sur les objets de base de données spécifique par le simple fait d’avoir l’autorisation VIEW SERVER STATE et en évitant une autorisation spécifique à la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
