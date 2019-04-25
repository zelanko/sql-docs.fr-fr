---
title: dbo.syssessions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syssessions_TSQL
- dbo.syssessions
- syssessions_TSQL
- syssessions
dev_langs:
- TSQL
helpviewer_keywords:
- syssessions system table
ms.assetid: 187819b6-c7f4-4a26-b74c-0a89e96695cf
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2ad2ccc2505c3bb72b8d2efc02afbc5ef5aebaf0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470553"
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Chaque fois que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] démarre, il crée une nouvelle session. L'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des sessions pour préserver l'état des travaux lorsque le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent redémarre ou s'arrête inopinément. Chaque ligne de la **syssessions** table contient des informations sur une seule session. Utilisez le **sysjobactivity** table pour afficher l’état du travail à la fin de chaque session.  
  
 Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**Int**|ID d'une session de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**agent_start_date**|**datetime**|Date et heure du démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour cette session.|  
  
## <a name="remarks"></a>Notes  
 Seuls les utilisateurs qui sont membres de la **sysadmin** rôle serveur fixe peut accéder à cette table.  
  
## <a name="see-also"></a>Voir aussi  
 [dbo.sysjobactivity &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
