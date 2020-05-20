---
title: sys. dm_tran_commit_table (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_tran_commit_table
- dm_tran_commit_table_TSQL
- sys.dm_tran_commit_table
- sys.dm_tran_commit_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_commit_table dynamic management view
ms.assetid: 732d23c5-1f6c-4e96-bc85-8f29b520cf0e
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 84278124664b72c45e038de7981057eaff1014f0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82819809"
---
# <a name="change-tracking---sysdm_tran_commit_table"></a>Change Tracking-sys. dm_tran_commit_table
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Affiche une ligne pour chaque transaction validée pour une table suivie par le suivi des modifications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La vue de gestion sys.dm_tran_commit_table, fournie à des fins de prise en charge, expose les informations relatives aux transactions que le suivi des modifications stocke dans la table système sys.syscommittab. La table sys.syscommittab fournit un mappage persistant efficace d'un ID de transaction spécifique à la base de données au numéro séquentiel dans le journal de validation (LSN) et l'horodateur de validation de la transaction. Les données stockées dans la table sys.syscommittab et exposées dans cette vue de gestion sont soumises au nettoyage en fonction de la période de rétention spécifiée lors de la configuration du suivi des modifications.  
  
> [!NOTE]  
>  Pour appeler cette valeur à partir de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , utilisez le nom **sys. dm_pdw_nodes_tran_commit_table**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|commit_ts|**bigint**|Nombre à croissance monotone servant d'horodateur spécifique à la base de données pour chaque transaction validée.|  
|xdes_id|**bigint**|ID interne spécifique à la base de données pour la transaction.|  
|commit_lbn|**bigint**|Numéro du bloc de journal qui contient l'enregistrement du journal de validation de la transaction.|  
|commit_csn|**bigint**|Numéro séquentiel de validation spécifique à l'instance pour la transaction.|  
|commit_time|**smalldatetime**|Heure de la validation de la transaction.|  
|pdw_node_id|**int**|**S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ,[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues et fonctions de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [À propos du suivi des modifications &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
  


