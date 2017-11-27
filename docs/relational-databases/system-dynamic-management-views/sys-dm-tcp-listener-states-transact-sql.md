---
title: Sys.dm_tcp_listener_states (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_tcp_listener_states
- dm_tcp_listener_states
- sys.dm_tcp_listener_states_TSQL
- dm_tcp_listener_states_TSQL
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], listeners
- sys.dm_tcp_listener_states dynamic management view
ms.assetid: 9997ffed-a4c1-428f-8bac-3b9e4b16d7cf
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d111ae8b610ca54516181fa6cfd6492b45d23211
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmtcplistenerstates-transact-sql"></a>sys.dm_tcp_listener_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne contenant les informations dynamiques d'état pour chaque écouteur TCP.  
  
> [!NOTE]
> L'écouteur du groupe de disponibilité peut écouter le même port que l'écouteur de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dans ce cas, les écouteurs sont répertoriées séparément, de la même façon que pour un écouteur Service Broker.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**listener_id**|**int**|ID interne de l'écouteur. N'accepte pas la valeur NULL.<br /><br /> Clé primaire.|  
|**« adresse_IP »**|**nvarchar48**|Adresse IP d'écouteur en ligne et actuellement écoutée. Les adresses IPv4 et IPv6 sont autorisées. Si un écouteur possède les deux types d'adresses, ils sont répertoriés séparément. Un caractère générique IPv4 est affiché en tant que « 0.0.0.0 ». Un caractère générique IPv6 est affiché en tant que « :: ».<br /><br /> N'accepte pas la valeur NULL.|  
|**is_ipv4**|**bit**|Type d'adresse IP<br /><br /> 1 = IPv4<br /><br /> 0 = IPv6|  
|**port**|**int**|Numéro de port sur lequel l'écouteur écoute. N'accepte pas la valeur NULL.|  
|**type**|**tinyint**|Type d'écouteur, un des suivants :<br /><br /> 0 = [!INCLUDE[tsql](../../includes/tsql-md.md)]<br /><br /> 1 = Service Broker<br /><br /> 2 = Mise en miroir de la base de données<br /><br /> N'accepte pas la valeur NULL.|  
|**type_desc**|**nvarchar (20)**|Description de la **type**, un des :<br /><br /> TSQL<br /><br /> SERVICE_BROKER<br /><br /> DATABASE_MIRRORING<br /><br /> N'accepte pas la valeur NULL.|  
|**état**|**tinyint**|État de l'écouteur du groupe de disponibilité, un des suivants :<br /><br /> 1 = En ligne. L'écouteur écoute et traite les demandes.<br /><br /> 2 = Redémarrage en attente. L'écouteur est hors connexion, en attente d'un redémarrage.<br /><br /> Si l'écouteur du groupe de disponibilité écoute sur le même port que l'instance de serveur, ces deux écouteurs ont toujours le même état.<br /><br /> N'accepte pas la valeur NULL.<br /><br /> Remarque : Les valeurs de cette colonne proviennent de l’objet TSD_listener. La colonne ne prend pas en charge un état hors connexion, car lorsque le TDS_listener est hors connexion, il ne peut pas être interrogé pour l’état.|  
|**state_desc**|**nvarchar(16)**|Description de **état**, un des :<br /><br /> ONLINE<br /><br /> PENDING_RESTART<br /><br /> N'accepte pas la valeur NULL.|  
|**heure_début**|**datetime**|Horodateur qui indique quand l'écouteur a été démarré. N'accepte pas la valeur NULL.|  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation des catalogues système SQL Server FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Affichages catalogue des groupes de disponibilité Always On &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Toujours sur les fonctions et vues de gestion dynamique de groupes de disponibilité &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)  
  
  
