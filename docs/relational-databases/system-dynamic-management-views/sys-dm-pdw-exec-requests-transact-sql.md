---
title: sys.dm_pdw_exec_requests (Transact-SQL) Microsoft Docs
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
ms.openlocfilehash: 4f4ebcbf84da7d899b4d4cbd861cfb2ae3f75863
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82087559"
---
# <a name="sysdm_pdw_exec_requests-transact-sql"></a>sys.dm_pdw_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Détient des informations sur toutes [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]les demandes actuellement ou récemment actives dans . Il énumère une rangée par demande/requête.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Clé pour ce point de vue. ID numérique unique associé à la demande.|Unique dans toutes les demandes du système.|  
|session_id|**nvarchar(32)**|ID numérique unique associé à la session dans laquelle cette requête a été exécutée. Voir [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|État actuel de la demande.|'Running', 'Suspended', 'Completed', 'Canceled', 'Failed'.|  
|submit_time|**datetime**|Heure à laquelle la demande a été soumise pour exécution.|Date **de validité** plus petite ou égale à l’heure actuelle et start_time.|  
|start_time|**datetime**|Heure à laquelle l’exécution de la demande a été lancée.|NULL pour les demandes en file d’attente; autrement, **date de validité** plus petite ou égale à l’heure actuelle.|  
|end_compile_time|**datetime**|Heure à laquelle le moteur a terminé la compilation de la demande.|NULL pour les demandes qui n’ont pas encore été compilées; autrement une **date valide** inférieure à start_time et moins ou égale à l’heure actuelle.|
|end_time|**datetime**|Heure à laquelle l’exécution de la demande a été complétée, a échoué ou a été annulée.|Null pour les demandes en file d’attente ou actives; autrement, une **date de validité** plus petite ou égale à l’heure actuelle.|  
|total_elapsed_time|**int**|Le temps s’est écoulé dans l’exécution depuis que la demande a été commencée, en millisecondes.|Entre 0 et la différence entre start_time et end_time.</br></br> Si total_elapsed_time dépasse la valeur maximale d’un intégré, total_elapsed_time continuera d’être la valeur maximale. Cette condition générera l’avertissement "La valeur maximale a été dépassée."</br></br> La valeur maximale en millisecondes est la même que 24,8 jours.|  
|label|**nvarchar(255)**|Chaîne d’étiquettes facultative associée à certaines déclarations de requête SELECT.|Toute chaîne contenant 'a-z','A-Z','0-9','.'.|  
|error_id|**nvarchar(36)**|ID unique de l’erreur associée à la demande, le cas échéant.|Voir [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); réglé à NULL si aucune erreur n’a eu lieu.|  
|database_id|**int**|Identification de la base de données utilisée par le contexte explicite (par exemple, USE DB_X).|Voir ID dans [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|command|**nvarchar(4000)**|Détient le texte intégral de la demande tel que soumis par l’utilisateur.|Toute requête ou texte valide de demande. Les requêtes de plus de 4000 octets sont tronquées.|  
|resource_class|**nvarchar(20)**|Le groupe de charge de travail utilisé pour cette demande. |Classes de ressources statiques</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>Classes de ressources dynamiques</br>SmallRC (en)</br>MediumRC (MediumRC)</br>Grand CR</br>XLargeRC (en)|
|importance|**nvarchar(128)**|L’importance fixant la demande exécutée à.  C’est l’importance relative d’une demande dans ce groupe de charge de travail et dans les groupes de charge de travail pour les ressources partagées.  L’importance spécifiée dans le classificateur remplace le cadre d’importance du groupe de charge de travail.</br>S’applique à : Azure SQL Data Warehouse|NULL</br>low</br>below_normal</br>normal (par défaut)</br>above_normal</br>high|
|group_name|**sysname** |Pour les demandes utilisant des ressources, group_name est le nom du groupe de charge de travail que la demande est en cours d’exécution sous.  Si la demande n’utilise pas les ressources, group_name est nulle.</br>S’applique à : Azure SQL Data Warehouse|
|classifier_name|**sysname**|Pour les demandes utilisant des ressources, Le nom du classificateur utilisé pour attribuer des ressources et de l’importance.||
|resource_allocation_percentage|**décimale(5,2)**|Le pourcentage de ressources allouées à la demande.</br>S’applique à : Azure SQL Data Warehouse|
|result_cache_hit|**Hexadécimal**|Détail sur la question de savoir si une requête complétée a utilisé le cache de résultat.  </br>S’applique à : Azure SQL Data Warehouse| 1 - Résultat set cache hit </br> 0 - Définir de résultat cache miss </br> Valeurs négatives - Raisons pour lesquelles la mise en cache des résultats n’a pas été utilisée.  Voir la section remarques pour plus de détails.|
||||
  
## <a name="remarks"></a>Notes 
 Pour plus d’informations sur les lignes maximales retenues par cette vue, consultez la section Métadonnées dans le sujet [des limites de capacité.](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata)

 Le result_cache_hit est un peumask de l’utilisation d’une requête de cache de jeu de résultat.  Cette colonne peut être [la (Bitwise OU)](../../t-sql/language-elements/bitwise-or-transact-sql.md) produit d’une ou plusieurs de ces valeurs :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Résultat set cache hit|  
|-**0x00**|Résultat set cache miss|  
|-**0x01 (en)**|La mise en cache des ensembles de résultats est désactivée dans la base de données.|  
|-**0x02**|La mise en cache des résultats est désactivée au cours de la session. | 
|-**0x04**|La mise en cache des ensembles de résultats est désactivée en raison de l’absence de sources de données pour la requête.|  
|-**0x08**|La mise en cache des ensembles de résultats est désactivée en raison des prédicats de sécurité au niveau de la ligne.|  
|-**0x10**|La mise en cache des ensembles de résultats est désactivée en raison de l’utilisation d’une table système, d’une table temporaire ou d’une table externe dans la requête.|  
|-**0x20**|La mise en cache des ensembles de résultats est désactivée parce que la requête contient des constantes de temps d’exécution, des fonctions définies par l’utilisateur ou des fonctions non déterministes.|  
|-**0x40**|La mise en cache des résultats est désactivée en raison de la taille estimée de l’ensemble de résultats est >10 Go.|  
|-**0x80**|La mise en cache des ensembles de résultats est désactivée parce que l’ensemble de résultats contient des lignes de grande taille (>64kb).|  
  
## <a name="permissions"></a>Autorisations

 Requiert l'autorisation VIEW SERVER STATE.  
  
## <a name="security"></a>Sécurité

 sys.dm_pdw_exec_requests ne filtre pas les résultats des requêtes selon les autorisations spécifiques à la base de données. Les connexions avec l’autorisation VIEW SERVER STATE peuvent obtenir les résultats des requêtes pour toutes les bases de données  
  
>[!WARNING]  
>Un attaquant peut utiliser sys.dm_pdw_exec_requests pour récupérer des informations sur des objets de base de données spécifiques en ayant simplement l’autorisation VIEW SERVER STATE et en n’ayant pas d’autorisation spécifique à la base de données.  
  
## <a name="see-also"></a>Voir aussi

 [SQL Data Warehouse et Parallel Data Warehouse Dynamic Management Views &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)
