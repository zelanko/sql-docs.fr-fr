---
title: MSsubscriber_info (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSsubscriber_info_TSQL
- MSsubscriber_info
dev_langs: TSQL
helpviewer_keywords: MSsubscriber_info system table
ms.assetid: 5ca22f41-6020-4f72-8110-e69baf3447cb
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: acbbf203509f1d2ddd4c3604e8cfce8067132d76
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssubscriberinfo-transact-sql"></a>MSsubscriber_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSsubscriber_info** table contient une ligne pour chaque paire de serveur de publication/abonné, objet d’abonnements envoyé à partir du serveur de distribution local. Cette table est stockée dans la base de données de distribution.  
  
 **Remarque** cette table système est déconseillée et est maintenue afin de prendre en charge les versions précédentes de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="definition"></a>Définition  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**publisher** (serveur de publication)|**sysname**|Le nom du serveur de publication.|  
|**subscriber** (Abonné)|**sysname**|Nom de l'Abonné.|  
|**type**|**tinyint**|Type d'abonné :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonné.<br /><br /> **1** = source de données ODBC.|  
|**connexion**|**sysname**|Connexion pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Stocké sous forme chiffrée si l'Abonné est ajouté à l'aide du mode d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**mot de passe**|**nvarchar (524)**|Mot de passe pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Stocké sous forme chiffrée si l'Abonné est ajouté à l'aide du mode d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Description**|**nvarchar(255)**|Description de l'abonné.|  
|**security_mode**|**int**|Mode de sécurité implémenté :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] l’authentification Windows.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
