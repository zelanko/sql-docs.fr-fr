---
title: Sys.dm_hadr_auto_page_repair (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
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
- dm_hadr_auto_page_repair_TSQL
- sys.dm_hadr_auto_page_repair
- sys.dm_hadr_auto_page_repair_TSQL
- dm_hadr_auto_page_repair
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- automatic page repair
- sys.dm_hadr_auto_page_repair dynamic management view
ms.assetid: d7840adf-4a1b-41ac-bc94-102c07ad1c79
caps.latest.revision: "8"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a29d92e0309ed4ff9379e0d3370f1f1a299e512
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmhadrautopagerepair-transact-sql"></a>sys.dm_hadr_auto_page_repair (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque tentative de réparation de page automatique sur une base de données de disponibilité sur un réplica de disponibilité hébergé pour un groupe de disponibilité quelconque par l'instance de serveur. Cette vue contient des lignes pour les tentatives de réparation de page automatique les plus récentes sur une base de données primaire ou secondaire donnée, avec un maximum de 100 lignes par base de données. Dès qu'une base de données atteint le maximum, la ligne pour sa tentative de réparation de page automatique suivante remplace l'une des entrées existantes. Le tableau suivant définit la signification des différentes colonnes.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID de la base de données à laquelle cette ligne correspond.|  
|**FILE_ID**|**int**|ID du fichier dans lequel la page est située.|  
|**PAGE_ID**|**bigint**|ID de la page dans le fichier.|  
|**error_type**|**int**|Type de l'erreur. Les valeurs peuvent être :<br /><br /> **-**1 = toutes les erreurs 823 de matériel<br /><br /> 1 = 824 erreurs autre qu’une somme de contrôle incorrecte ou d’une page endommagée (par exemple, un ID de page incorrect)<br /><br /> 2 = Somme de contrôle incorrecte<br /><br /> 3 = Page endommagée|  
|**page_status**|**int**|État de la tentative de réparation de page :<br /><br /> 2 = En file d'attente pour demande au serveur partenaire.<br /><br /> 3 = Demande envoyée au serveur partenaire.<br /><br /> 4 = En file d'attente pour réparation de page automatique (réponse reçue du serveur partenaire).<br /><br /> 5 = Réparation de page automatique réussie et la page doit être utilisable.<br /><br /> 6 = Irréparable. Cela indique qu'une erreur a eu lieu pendant la tentative de réparation de page, par exemple, parce que la page est également endommagée sur le serveur partenaire, le serveur partenaire est déconnecté ou un problème réseau s'est produit. Cet état n'est pas terminal ; si la page est de nouveau endommagée, elle sera redemandée au serveur partenaire.|  
|**modification_time**|**datetime**|Heure de la dernière modification de l'état de page.|  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Réparation de page automatique &#40;groupes de disponibilité : mise en miroir de bases de données&#41;](../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [suspect_pages &#40; Transact-SQL &#41;](../../relational-databases/system-tables/suspect-pages-transact-sql.md)   
 [Gérer la table suspect_pages &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  

