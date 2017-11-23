---
title: dbo.syssessions (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.syssessions_TSQL
- dbo.syssessions
- syssessions_TSQL
- syssessions
dev_langs: TSQL
helpviewer_keywords: syssessions system table
ms.assetid: 187819b6-c7f4-4a26-b74c-0a89e96695cf
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 140d81eef1b0f6b745e5f889b7889c265820405c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Chaque fois que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] démarre, il crée une nouvelle session. L'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des sessions pour préserver l'état des travaux lorsque le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent redémarre ou s'arrête inopinément. Chaque ligne de la **syssessions** table contient des informations sur une seule session. Utilisez le **sysjobactivity** table pour afficher l’état du travail à la fin de chaque session.  
  
 Cette table est stockée dans le **msdb** base de données.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|ID d'une session de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**agent_start_date**|**datetime**|Date et heure du démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour cette session.|  
  
## <a name="remarks"></a>Notes  
 Seuls les utilisateurs qui sont membres de la **sysadmin** rôle serveur fixe peut accéder à cette table.  
  
## <a name="see-also"></a>Voir aussi  
 [dbo.sysjobactivity &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
