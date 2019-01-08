---
title: affinity64 mask (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- processor affinity [SQL Server]
- affinity64 mask option
- binding processors [SQL Server]
ms.assetid: 75ed08c7-f85c-4e15-9ee1-e7bc545d3293
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 20e4cf3af48fa560293a9de05e768410d561a33b
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52641180"
---
# <a name="affinity64-mask-server-configuration-option"></a>affinity64 mask (option de configuration de serveur)
  L'option affinity64 mask lie des processeurs à des threads spécifiques, à l'image de l'option affinity mask. Utilisez l'option affinity mask pour lier les 32 premiers processeurs et l'option affinity64 mask pour lier les processeurs restants de l'ordinateur. Cette option est visible uniquement sur la version 64 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)] Utilisez plutôt [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Masque d'affinité (option de configuration de serveur)](affinity-mask-server-configuration-option.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
