---
title: dbo. syssessions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2019
ms.prod: sql
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
ms.openlocfilehash: 566445a3680dc54382a7e3e66bf77dbcbddca2e8
ms.sourcegitcommit: 4933934fad9f3c3e16406952ed964fbd362ee086
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548284"
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Chaque fois que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] démarre, il crée une nouvelle session. L'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des sessions pour préserver l'état des travaux lorsque le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent redémarre ou s'arrête inopinément. Chaque ligne de la table **syssessions** contient des informations sur une session. Utilisez la table **sysjobactivity** pour afficher l’état du travail à la fin de chaque session.  
  
 Cette table est stockée dans la base de données **msdb** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**tiers**|ID d'une session de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette session_id n’est pas le SPID pour la session, mais plutôt une valeur d’identité dans cette table système.|  
|**agent_start_date**|**Date/heure**|Date et heure du démarrage du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour cette session.|  
  
## <a name="remarks"></a>Remarques  
 Seuls les utilisateurs qui sont membres du rôle serveur fixe **sysadmin** peuvent accéder à cette table.  
  
## <a name="see-also"></a>Voir aussi  
 [dbo. sysjobactivity &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
