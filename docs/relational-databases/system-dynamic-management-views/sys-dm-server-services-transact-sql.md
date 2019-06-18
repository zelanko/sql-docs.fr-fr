---
title: sys.dm_server_services (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_server_services
- sys.dm_server_services
- sys.dm_server_services_TSQL
- dm_server_services_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_services dynamic management view
ms.assetid: 3f0defd0-478d-4e7f-96be-8795c9de4e3f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8acb2fae0aa0edadf1995a0a103ff60b66a912a9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62686222"
---
# <a name="sysdmserverservices-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations relatives aux services SQL Server, Texte intégral et Agent SQL Server dans l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez cette vue de gestion dynamique pour signaler des informations d'état sur ces services.  
  
 
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar (256)**|Nom de la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], recherche en texte intégral ou service SQL Server Agent. Ne peut pas avoir la valeur null.|  
|startup_type|**Int**|Indique le mode de démarrage du service. Voici les valeurs possibles et leurs descriptions correspondantes.<br /><br /> 0 : Autres<br />1 : Autres<br />2 : Automatic<br />3 : Manuel<br />4 : Désactivé<br /><br /> Autorise la valeur NULL.|  
|startup_desc|**nvarchar (256)**|Décrit le mode de démarrage du service. Voici les valeurs possibles et leurs descriptions correspondantes.<br /><br /> Autres : Autre (démarrage)<br />Autres : Autre (démarrage système)<br />Automatique : Démarrage automatique<br />Manuelle : Début de la demande<br />Désactivé : Désactivé<br /><br /> Ne peut pas avoir la valeur null.|  
|status|**Int**|Indique l'état actuel du service. Voici les valeurs possibles et leurs descriptions correspondantes.<br /><br /> 1 : Arrêté<br />2 : Autre (démarrage en attente)<br />3 : Autre (arrêt en attente)<br />4 : Exécution en cours<br />5 : Autre (continuation en attente)<br />6: Autre (suspension en attente)<br />7: Suspendu<br /><br /> Autorise la valeur NULL.|  
|status_desc|**nvarchar (256)**|Décrit l'état actuel du service. Voici les valeurs possibles et leurs descriptions correspondantes.<br /><br /> Arrêté : Le service est arrêté.<br />Autre (démarrage de l’opération en attente) : Le service est en cours de démarrage.<br />Autre (opération d’arrêt en attente) : Le service est en cours d’arrêt.<br />En cours d’exécution : Le service est en cours d'exécution.<br />Autres (continuer les opérations en attente) : Le service est en état d’attente.<br />Autre (suspension en attente) : Le service est en cours de suspension.<br />Suspendu : Le service est suspendu.<br /><br /> Ne peut pas avoir la valeur null.|  
|process_id|**Int**|ID de processus du service. Ne peut pas avoir la valeur null.|  
|last_startup_time|**datetimeoffset(7)**|Date et heure du dernier démarrage du service. Autorise la valeur NULL.|  
|service_account|**nvarchar (256)**|Compte autorisé à contrôler le service. Ce compte peut démarrer ou arrêter le service ou modifier ses propriétés. Ne peut pas avoir la valeur null.|  
|filename|**nvarchar (256)**|Chemin d'accès et nom de fichier de l'exécutable du service. Ne peut pas avoir la valeur null.|  
|is_clustered|**nvarchar(1)**|Indique si le service est installé en tant que ressource d'un serveur en cluster. Ne peut pas avoir la valeur null.|  
|cluster_nodename|**nvarchar (256)**|Nom du nœud de cluster sur lequel le service est installé. Autorise la valeur NULL.|
|instant_file_initialization_enabled|**nvarchar(1)**|Spécifie si l’initialisation instantanée des fichiers est activée pour le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.<br /><br />Y = initialisation instantanée des fichiers est activée pour le service.<br /><br />N = initialisation instantanée des fichiers est désactivée pour le service.<br /><br /> Autorise la valeur NULL.<br /><br /> **Remarque :** Ne s’applique pas à d’autres services tels que l’Agent SQL Server.<br /><br /> **S’applique à :** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (En commençant par [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4, et [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).|  

## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation `VIEW SERVER STATE` sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_server_registry &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  
