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
ms.openlocfilehash: b1c44b269f68b39d633a18f366615fd41b582938
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892952"
---
# <a name="sysdm_server_services-transact-sql"></a>sys.dm_server_services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations relatives aux services SQL Server, Texte intégral et Agent SQL Server dans l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez cette vue de gestion dynamique pour signaler des informations d'état sur ces services.  
  
 
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar (256)**|Nom du service [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], de texte intégral ou de SQL Server Agent. Ne peut pas avoir la valeur null.|  
|startup_type|**int**|Indique le mode de démarrage du service. Voici les valeurs possibles et leurs descriptions correspondantes.<br /><br /> 0 : Autre<br />1 : Autre<br />2 : Automatique<br />3 : Manuel<br />4 : Désactivé<br /><br /> Autorise la valeur NULL.|  
|startup_type_desc|**nvarchar (256)**|Décrit le mode de démarrage du service. Voici les valeurs possibles et leurs descriptions correspondantes.<br /><br /> Autres Autre (démarrage)<br />Autres Autre (démarrage système)<br />Automatique: Démarrage automatique<br />Manuelle: Début de la demande<br />Désactivé : Désactivé<br /><br /> Ne peut pas avoir la valeur null.|  
|status|**int**|Indique l'état actuel du service. Voici les valeurs possibles et leurs descriptions correspondantes.<br /><br /> 1 : Arrêté<br />2 : Autre (démarrage en attente)<br />3 : Autre (arrêt en attente)<br />4 : Exécution<br />5 : Autre (toujours en attente)<br />6,3 Autre (pause en attente)<br />Commission(7 Suspendu<br /><br /> Autorise la valeur NULL.|  
|status_desc|**nvarchar (256)**|Décrit l'état actuel du service. Voici les valeurs possibles et leurs descriptions correspondantes.<br /><br /> Mis Le service est arrêté.<br />Autre (opération de démarrage en attente): Le service est en cours de démarrage.<br />Autre (opération d’arrêt en attente): Le service est en cours d’arrêt.<br />Marche Le service est en cours d'exécution.<br />Autre (opérations de reprise en attente): Le service est dans un état d’attente.<br />Autre (pause en attente): Le service est en cours de suspension.<br />Suspendu Le service est suspendu.<br /><br /> Ne peut pas avoir la valeur null.|  
|process_id|**int**|ID de processus du service. Ne peut pas avoir la valeur null.|  
|last_startup_time|**datetimeoffset(7)**|Date et heure du dernier démarrage du service. Autorise la valeur NULL.|  
|service_account|**nvarchar (256)**|Compte autorisé à contrôler le service. Ce compte peut démarrer ou arrêter le service ou modifier ses propriétés. Ne peut pas avoir la valeur null.|  
|filename|**nvarchar (256)**|Chemin d'accès et nom de fichier de l'exécutable du service. Ne peut pas avoir la valeur null.|  
|is_clustered|**nvarchar(1)**|Indique si le service est installé en tant que ressource d'un serveur en cluster. Ne peut pas avoir la valeur null.|  
|cluster_nodename|**nvarchar (256)**|Nom du nœud de cluster sur lequel le service est installé. Autorise la valeur NULL.|
|instant_file_initialization_enabled|**nvarchar(1)**|Spécifie si l’initialisation instantanée des fichiers est activée [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] pour le service.<br /><br />Y = l’initialisation instantanée des fichiers est activée pour le service.<br /><br />N = l’initialisation instantanée des fichiers est désactivée pour le service.<br /><br /> Autorise la valeur NULL.<br /><br /> **Remarque :** Ne s’applique pas à d’autres services tels que le SQL Server Agent.<br /><br /> **S’applique à :** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](À partir [!INCLUDE[sssql11](../../includes/sssql11-md.md)] de SP4 et [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 jusqu' [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]à).|  

## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation `VIEW SERVER STATE` sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_server_registry &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  
