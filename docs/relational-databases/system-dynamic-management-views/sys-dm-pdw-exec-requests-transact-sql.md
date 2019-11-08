---
title: sys. dm_pdw_exec_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 15d27881378a88c8f4ae6d65640be6218ecd3530
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632768"
---
# <a name="sysdm_pdw_exec_requests-transact-sql"></a>sys. dm_pdw_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les demandes actuellement ou récemment actives dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Elle répertorie une ligne par requête/requête.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Clé pour cette vue. ID numérique unique associé à la demande.|Unique pour toutes les demandes dans le système.|  
|session_id|**nvarchar(32)**|ID numérique unique associé à la session dans laquelle cette requête a été exécutée. Consultez [sys. dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|État actuel de la demande.|« Running », « Suspended », « Completed », « Canceled », « failed ».|  
|submit_time|**datetime**|Heure à laquelle la demande a été soumise pour exécution.|**DateTime** valide, plus petit ou égal à l’heure actuelle et à la start_time.|  
|start_time|**datetime**|Heure à laquelle l’exécution de la requête a été démarrée.|NULL pour les demandes mises en file d’attente ; dans le cas contraire, la valeur **DateTime** valide est inférieure ou égale à l’heure actuelle.|  
|end_compile_time|**datetime**|Heure à laquelle le moteur a terminé la compilation de la requête.|NULL pour les requêtes qui n’ont pas encore été compilées ; Sinon, une valeur **DateTime** valide inférieure à start_time et inférieure ou égale à l’heure actuelle.|
|end_time|**datetime**|Heure à laquelle l’exécution de la requête s’est terminée, a échoué ou a été annulée.|NULL pour les demandes en file d’attente ou actives ; dans le cas contraire, un **DateTime** valide est plus petit ou égal à l’heure actuelle.|  
|total_elapsed_time|**int**|Temps écoulé durant l’exécution depuis le début de la demande, en millisecondes.|Entre 0 et la différence entre start_time et end_time.</br></br> Si total_elapsed_time dépasse la valeur maximale d’un entier, total_elapsed_time sera toujours la valeur maximale. Cette condition génère l’avertissement « la valeur maximale a été dépassée ».</br></br> La valeur maximale en millisecondes est identique à 24,8 jours.|  
|Noms|**nvarchar(255)**|Chaîne d’étiquette facultative associée à certaines instructions de requête SELECT.|Toute chaîne contenant « a-z », « A-Z », « 0-9 », « _ ».|  
|error_id|**nvarchar (36)**|ID unique de l’erreur associée à la demande, le cas échéant.|Consultez [sys. dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); Affectez la valeur NULL si aucune erreur ne s’est produite.|  
|database_id|**int**|Identificateur de la base de données utilisée par le contexte explicite (par exemple, utilisez DB_X).|Consultez ID dans [sys. databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|commande|**nvarchar(4000)**|Contient le texte complet de la demande, tel qu’il est soumis par l’utilisateur.|Tout texte de requête ou de requête valide. Les requêtes dont la taille est supérieure à 4000 octets sont tronquées.|  
|resource_class|**nvarchar(20**|Groupe de charge de travail utilisé pour cette demande. |Classes de ressources statiques</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>Classes de ressources dynamiques</br>SmallRC</br>MediumRC</br>LargeRC</br>XLargeRC|
|importance|**nvarchar(128)**|Importance du paramètre de requête exécutée sur.  Il s’agit de l’importance relative d’une demande dans ce groupe de charges de travail et entre les groupes de charge de travail pour les ressources partagées.  L’importance spécifiée dans le classifieur remplace le paramètre d’importance du groupe de charge de travail.</br>S’applique à : Azure SQL Data Warehouse|NULL</br>low</br>below_normal</br>normal (par défaut)</br>above_normal</br>high|
|group_name|**sysname** |Pour les demandes qui utilisent des ressources, group_name est le nom du groupe de charge de travail sous lequel la requête s’exécute.  Si la demande n’utilise pas de ressources, group_name a la valeur null.</br>S’applique à : Azure SQL Data Warehouse|
|classifier_name|**sysname**|Pour les demandes qui utilisent des ressources, nom du classifieur utilisé pour assigner des ressources et leur importance.||
|resource_allocation_percentage|**décimal (5, 2)**|Pourcentage de ressources allouées à la demande.</br>S’applique à : Azure SQL Data Warehouse|
|result_set_cache|**bit**|Indique si une requête terminée était un accès au cache des résultats (1) ou non (0). </br>S’applique à : Azure SQL Data Warehouse|0, 1|
||||
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez la section métadonnées dans la rubrique [limites de capacité](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .
  
## <a name="permissions"></a>Autorisations

 Requiert l'autorisation VIEW SERVER STATE.  
  
## <a name="security"></a>Sécurité

 sys. dm_pdw_exec_requests ne filtre pas les résultats de la requête en fonction des autorisations spécifiques à la base de données. Les connexions avec l’autorisation VIEW SERVER STATE peuvent obtenir des résultats de requête de résultats pour toutes les bases de données  
  
>[!WARNING]  
>Une personne malveillante peut utiliser sys. dm_pdw_exec_requests pour récupérer des informations sur des objets de base de données spécifiques en ayant simplement l’autorisation VIEW SERVER STATE et en n’ayant pas d’autorisation propre à la base de données.  
  
## <a name="see-also"></a>Voir aussi

 [SQL Data Warehouse et Parallel Data Warehouse vues &#40;de gestion dynamique Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)
