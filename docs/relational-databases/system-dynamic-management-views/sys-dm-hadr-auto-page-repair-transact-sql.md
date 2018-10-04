---
title: Sys.dm_hadr_auto_page_repair (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_hadr_auto_page_repair_TSQL
- sys.dm_hadr_auto_page_repair
- sys.dm_hadr_auto_page_repair_TSQL
- dm_hadr_auto_page_repair
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- automatic page repair
- sys.dm_hadr_auto_page_repair dynamic management view
ms.assetid: d7840adf-4a1b-41ac-bc94-102c07ad1c79
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: be4bd3af61ef81c81dffc695ed3489c620b42903
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47688227"
---
# <a name="sysdmhadrautopagerepair-transact-sql"></a>sys.dm_hadr_auto_page_repair (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque tentative de réparation de page automatique sur une base de données de disponibilité sur un réplica de disponibilité hébergé pour un groupe de disponibilité quelconque par l'instance de serveur. Cette vue contient des lignes pour les tentatives de réparation de page automatique les plus récentes sur une base de données primaire ou secondaire donnée, avec un maximum de 100 lignes par base de données. Dès qu'une base de données atteint le maximum, la ligne pour sa tentative de réparation de page automatique suivante remplace l'une des entrées existantes.
  
  Le tableau suivant définit la signification des différentes colonnes :  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**Int**|ID de la base de données à laquelle cette ligne correspond.|  
|**file_id**|**Int**|ID du fichier dans lequel la page est située.|  
|**page_id**|**bigint**|ID de la page dans le fichier.|  
|**error_type**|**Int**|Type de l'erreur. Les valeurs peuvent être :<br /><br /> **-** 1 = toutes les erreurs 823 de matériel<br /><br /> 1 = 824 erreurs autre qu’une somme de contrôle incorrecte ou une page endommagée (par exemple, un ID de page incorrect)<br /><br /> 2 = Somme de contrôle incorrecte<br /><br /> 3 = Page endommagée|  
|**page_status**|**Int**|État de la tentative de réparation de page :<br /><br /> 2 = En file d'attente pour demande au serveur partenaire.<br /><br /> 3 = Demande envoyée au serveur partenaire.<br /><br /> 4 = En file d'attente pour réparation de page automatique (réponse reçue du serveur partenaire).<br /><br /> 5 = Réparation de page automatique réussie et la page doit être utilisable.<br /><br /> 6 = Irréparable. Cela indique qu'une erreur a eu lieu pendant la tentative de réparation de page, par exemple, parce que la page est également endommagée sur le serveur partenaire, le serveur partenaire est déconnecté ou un problème réseau s'est produit. Cet état n'est pas terminal ; si la page est de nouveau endommagée, elle sera redemandée au serveur partenaire.|  
|**modification_time**|**datetime**|Heure de la dernière modification de l'état de page.|  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Réparation de page automatique &#40;groupes de disponibilité : mise en miroir de bases de données&#41;](../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [suspect_pages &#40;Transact-SQL&#41;](../../relational-databases/system-tables/suspect-pages-transact-sql.md)   
 [Gérer la table suspect_pages &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  

