---
title: Sys.dm_clr_appdomains (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_clr_appdomains
- sys.dm_clr_appdomains
- dm_clr_appdomains_TSQL
- sys.dm_clr_appdomains_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_appdomains dynamic management dynamic management view
ms.assetid: 9fe0d4fd-950a-4274-a493-85e776278045
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3ebcda61d95cc5131048ab32701d9d68228646ea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138411"
---
# <a name="sysdmclrappdomains-transact-sql"></a>sys.dm_clr_appdomains (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie une ligne pour chaque domaine d'application du serveur. Domaine d’application (**AppDomain**) est une construction dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR) qui est l’unité d’isolation pour une application. Vous pouvez utiliser cette vue pour comprendre et dépanner les objets d’intégration de CLR qui sont exécutent dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Il existe plusieurs types d'objets de base de données managés d'intégration CLR. Pour obtenir des informations générales sur ces objets, consultez [création d’objets de base de données avec l’intégration du Common Language Runtime (CLR)](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md). Chaque fois que ces objets sont exécutés, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée un **AppDomain** dans lequel il peut charger et exécuter le code requis. Le niveau d’isolement pour un **AppDomain** est un **AppDomain** par base de données par le propriétaire. Autrement dit, tous les objets CLR détenus par un utilisateur sont toujours exécutés dans le même **AppDomain** par base de données (si un utilisateur a inscrit des objets de base de données CLR dans différentes bases de données, la base de données CLR objets s’exécuteront dans différents domaines d’application). Un **AppDomain** n’est pas détruit une fois que le code termine son exécution. Il est mis en cache dans la mémoire pour les prochaines exécutions. Cela améliore les performances.  
  
 Pour plus d’informations, consultez [domaines d’Application](https://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**appdomain_address**|**varbinary(8)**|Adresse de la **AppDomain**. Base de données tous les objets appartenant à un utilisateur sont toujours chargés dans le même **AppDomain**. Vous pouvez utiliser cette colonne pour rechercher tous les assemblys actuellement chargés dans ce **AppDomain** dans **sys.dm_clr_loaded_assemblies**.|  
|**appdomain_id**|**int**|ID de la **AppDomain**. Chaque **AppDomain** a un ID unique.|  
|**appdomain_name**|**varchar(386)**|Nom de la **AppDomain** tel qu’assigné par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**creation_time**|**datetime**|Heure à laquelle le **AppDomain** a été créé. Étant donné que **AppDomains** sont mis en cache et réutilisés pour de meilleures performances, **creation_time** n’est pas nécessairement le temps lorsque le code a été exécuté.|  
|**db_id**|**Int**|ID de la base de données dans lequel cet **AppDomain** a été créé. Code stocké dans deux bases de données ne peuvent pas partager une **AppDomain**.|  
|**user_id**|**Int**|ID de l’utilisateur dont les objets peuvent s’exécuter dans **AppDomain**.|  
|**state**|**nvarchar(128)**|Un descripteur pour l’état actuel de la **AppDomain**. Un domaine d'application AppDomain peut être dans différents états de sa création à sa suppression. Pour plus d'informations, consultez la section « Remarques » de cette rubrique.|  
|**strong_refcount**|**Int**|Nombre de références fortes au **AppDomain**. Cela reflète le nombre de lots qui utilisent ce en cours d’exécution **AppDomain**. Notez que l’exécution de cette vue créera un **refcount fort**; même si aucun code en cours d’exécution, **strong_refcount** a la valeur 1.|  
|**weak_refcount**|**int**|Nombre de références faibles au **AppDomain**. Cela indique le nombre d’objets à l’intérieur de la **AppDomain** sont mis en cache. Lorsque vous exécutez un objet de base de données managés, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] met en cache dans le **AppDomain** pour une réutilisation ultérieure. Cela améliore les performances.|  
|**cost**|**int**|Coût de la **AppDomain**. Plus le coût est élevé, plus la probabilité cela **AppDomain** est soit déchargé si la sollicitation de la mémoire. Coût dépend généralement de la quantité de mémoire est nécessaire pour recréer cette **AppDomain**.|  
|**value**|**Int**|Valeur de la **AppDomain**. La valeur est faible, plus la probabilité cela **AppDomain** est soit déchargé si la sollicitation de la mémoire. Valeur dépend généralement le nombre de connexions ou de lots sont à l’aide de ce **AppDomain**.|  
|**total_processor_time_ms**|**bigint**|Temps processeur total, en millisecondes, utilisé par tous les threads lors de l'exécution dans le domaine d'application actuel depuis le démarrage du processus. Cela équivaut à **System.AppDomain.MonitoringTotalProcessorTime**.|  
|**total_allocated_memory_kb**|**bigint**|Taille totale, en kilo-octets, de toutes les allocations mémoire faites par le domaine d'application depuis sa création, sans soustraction de la mémoire recueillie. Cela équivaut à **System.AppDomain.MonitoringTotalAllocatedMemorySize**.|  
|**survived_memory_kb**|**bigint**|Nombre de kilo-octets qui ont survécu à la dernière collection bloquante complète et connus pour être référencés par le domaine d'application actuel. Cela équivaut à **System.AppDomain.MonitoringSurvivedMemorySize**.|  
  
## <a name="remarks"></a>Notes  
 Il existe une relation un-à-mai entre **dm_clr_appdomains.appdomain_address** et **dm_clr_loaded_assemblies.appdomain_address**.  
  
 Les tableaux suivants possible de liste **état** leurs descriptions, les valeurs, et quand ils se produisent dans le **AppDomain** cycle de vie. Vous pouvez utiliser ces informations pour suivre le cycle de vie d’un **AppDomain** et repérer suspectes ou répétitives **AppDomain** instances déchargement, sans avoir à analyser le journal des événements Windows.  
  
## <a name="appdomain-initialization"></a>Initialisation du domaine d'application AppDomain  
  
|État|Description|  
|-----------|-----------------|  
|E_APPDOMAIN_CREATING|Le **AppDomain** est en cours de création.|  
  
## <a name="appdomain-usage"></a>Utilisation du domaine d'application AppDomain  
  
|État|Description|  
|-----------|-----------------|  
|E_APPDOMAIN_SHARED|Le runtime **AppDomain** est prêt à être utilisé par plusieurs utilisateurs.|  
|E_APPDOMAIN_SINGLEUSER|Le **AppDomain** est prêt à être utilisé dans les opérations DDL. Ceux-ci diffèrent d'E_APPDOMAIN_SHARED en ceci que les domaines d'application AppDomains partagés sont utilisés pour les exécutions d'intégration du CLR par opposition aux opérations DDL. Ces domaines d'application AppDomains sont isolés d'autres opérations simultanées.|  
|E_APPDOMAIN_DOOMED|Le **AppDomain** est planifié pour être déchargé, mais il existe actuellement des threads qui s’exécutent dans celui-ci.|  
  
## <a name="appdomain-cleanup"></a>Suppression du domaine d'application AppDomain  
  
|État|Description|  
|-----------|-----------------|  
|E_APPDOMAIN_UNLOADING|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a demandé que le CLR décharge le **AppDomain**, généralement parce que l’assembly qui contient les objets de base de données managés a été modifié ou supprimé.|  
|E_APPDOMAIN_UNLOADED|Le CLR a déchargé le **AppDomain**. Cela est généralement le résultat d’une procédure de remontée **ThreadAbort**, **OutOfMemory**, ou une exception non gérée dans le code utilisateur.|  
|E_APPDOMAIN_ENQUEUE_DESTROY|Le **AppDomain** a été déchargé dans le CLR et voué à être détruit par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|E_APPDOMAIN_DESTROY|Le **AppDomain** processus de destruction par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|E_APPDOMAIN_ZOMBIE|Le **AppDomain** a été détruite par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais pas toutes les références à la **AppDomain** ont été nettoyés.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation VIEW SERVER STATE sur la base de données.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre comment afficher les détails d’un **AppDomain** pour un assembly donné :  
  
```  
select appdomain_id, creation_time, db_id, user_id, state  
from sys.dm_clr_appdomains a  
where appdomain_address =   
(select appdomain_address   
 from sys.dm_clr_loaded_assemblies  
   where assembly_id = 500);  
```  
  
 L’exemple suivant montre comment afficher tous les assemblys dans une donnée **AppDomain**:  
  
```  
select a.name, a.assembly_id, a.permission_set_desc, a.is_visible, a.create_date, l.load_time   
from sys.dm_clr_loaded_assemblies as l   
inner join sys.assemblies as a  
on l.assembly_id = a.assembly_id  
where l.appdomain_address =   
(select appdomain_address   
from sys.dm_clr_appdomains  
where appdomain_id = 15);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.dm_clr_loaded_assemblies &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)   
 [Vues de gestion dynamique liées à Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
