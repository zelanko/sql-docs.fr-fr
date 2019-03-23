---
title: sys.dm_pdw_exec_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/19/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3ab6f627c096326ce5c56828777bb9baf386e81a
ms.sourcegitcommit: 20de089b6e23107c88fb38b9af9d22ab0c800038
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356452"
---
# <a name="sysdmpdwexecrequests-transact-sql"></a>sys.dm_pdw_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les demandes actuellement ou récemment active dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Elle répertorie une ligne par/requête de la demande.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Clé pour cette vue. ID numérique unique associé à la demande.|Unique pour toutes les requêtes dans le système.|  
|session_id|**nvarchar(32)**|ID numérique unique associé à la session dans laquelle cette requête a été exécutée. See [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|État actuel de la demande.|'Running', 'Suspended', 'Completed', 'Canceled', 'Failed'.|  
|submit_time|**datetime**|Heure à laquelle la demande a été soumise pour exécution.|Valide **datetime** inférieure ou égale à l’heure actuelle et start_time.|  
|start_time|**datetime**|Heure de début de l’exécution de la demande.|NULL pour les demandes en file d’attente ; Sinon, valide **datetime** inférieure ou égale à l’heure actuelle.|  
|end_compile_time|**datetime**|Heure à laquelle le moteur a terminé la compilation de la demande.|NULL pour les demandes qui n’ont pas été compilés encore ; sinon valide **datetime** start_time inférieure et inférieure ou égale à l’heure actuelle.|
|end_time|**datetime**|Heure à laquelle l’exécution de la requête terminée, a échoué ou a été annulée.|NULL pour les demandes en file d’attente ou actives ; Sinon, valide **datetime** inférieure ou égale à l’heure actuelle.|  
|total_elapsed_time|**Int**|Temps écoulé dans l’exécution dans la mesure où la demande a été démarrée, en millisecondes.|Comprise entre 0 et la différence entre start_time et end_time.</br></br> Si total_elapsed_time dépasse la valeur maximale d’un entier, total_elapsed_time continueront à être la valeur maximale. Cette condition génère l’avertissement « la valeur maximale a été dépassée. »</br></br> La valeur maximale en millisecondes est identique à 24,8 jours environ.|  
|Étiquette|**nvarchar(255)**|Chaîne d’étiquette facultative associée à des instructions de la requête SELECT.|Toute chaîne contenant 'a-z', 'A-Z','0-9', '_'.|  
|error_id|**nvarchar(36)**|ID unique de l’erreur associée à la demande, le cas échéant.|Consultez [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); la valeur NULL si aucune erreur ne s’est produite.|  
|database_id|**Int**|Identificateur de la base de données utilisée par le contexte explicite (par exemple, utilisez DB_X).|Consultez les ID dans [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|commande|**nvarchar(4000)**|Contient le texte intégral de la demande et soumis par l’utilisateur.|Tout texte de requête ou de requête valid. Requêtes qui comptent plus de 4 000 octets sont tronquées.|  
|resource_class|**nvarchar(20)**|La classe de ressources pour cette demande. Consultez lié **concurrency_slots_used** dans [sys.dm_pdw_resource_waits &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md).  Pour plus d’informations sur les classes de ressources, consultez [gestion des ressources de classes et de la charge de travail](https://docs.microsoft.com/azure/sql-data-warehouse/resource-classes-for-workload-management) |Classes de ressources statiques</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>Classes de ressources dynamiques</br>SmallRC</br>MediumRC</br>LargeRC</br>XLargeRC|
|importance (version préliminaire pour SQL Data Warehouse Gen2)|**nvarchar(32)**|L’importance de définition de la demande a été envoyée. Requêtes avec une importance inférieure reste en file d’attente dans un état suspendu, si les demandes d’importance plus élevées sont envoyés.  Requêtes avec une importance plus élevée s’exécutent avant les demandes importance inférieure qui ont été envoyées précédemment.  Pour plus d’informations sur l’importance, consultez [Importance de la charge de travail](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-workload-importance).  |NULL</br>low</br>below_normal</br>Normal</br>above_normal</br>high|
  
 Pour plus d’informations sur le nombre de lignes maximal conservé par cette vue, consultez « Minimum et valeurs maximales » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="permissions"></a>Autorisations

 Requiert l'autorisation VIEW SERVER STATE.  
  
## <a name="security"></a>Sécurité

 Sys.dm_pdw_exec_requests ne filtre pas les résultats de requête en fonction des autorisations spécifiques à la base de données. Connexions avec l’autorisation VIEW SERVER STATE peuvent obtenir des résultats les résultats de requête pour toutes les bases de données  
  
>[!WARNING]  
>Une personne malveillante peut utiliser sys.dm_pdw_exec_requests pour récupérer des informations sur les objets de base de données spécifique par le simple fait d’avoir l’autorisation VIEW SERVER STATE et en évitant une autorisation spécifique à la base de données.  
  
## <a name="see-also"></a>Voir aussi

 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md) 
