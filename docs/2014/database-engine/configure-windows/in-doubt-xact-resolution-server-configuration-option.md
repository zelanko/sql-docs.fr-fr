---
title: in-doubt xact resolution (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- distributed transactions [SQL Server], unresolved transactions
- unresolved transactions
- in-doubt xact resolution option
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c30ca21d997d95058e034dbe36d601b601670a4f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48058619"
---
# <a name="in-doubt-xact-resolution-server-configuration-option"></a>in-doubt xact resolution (option de configuration de serveur)
  Utilisez l’option **in-doubt xact resolution** pour contrôler le résultat par défaut des transactions que [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) ne peut pas résoudre. L'incapacité à résoudre des transactions peut être liée au temps d'inactivité MS DTC ou à un résultat de transaction inattendu au moment de la récupération.  
  
 Le tableau suivant récapitule les valeurs de résultat possibles pour résoudre une transaction incertaine.  
  
|Valeur du résultat|Description|  
|-------------------|-----------------|  
|0|Pas de présomption. La récupération échoue si MS DTC ne peut pas résoudre les transactions incertaines.|  
|1|Validation présumée. Toutes les transactions incertaines de MS DTC sont supposées être validées.|  
|2|Abandon présumé. Toutes les transactions incertaines de MS DTC sont supposées avoir échoué.|  
  
 Pour réduire l'éventualité d'un temps d'inactivité prolongé, l'administrateur peut décider de configurer cette option pour présumer la validation ou l'abandon, comme dans l'exemple suivant.  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 2 -– presume abort  
GO  
RECONFIGURE  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 L'administrateur peut aussi conserver la valeur par défaut (pas de présomption) et autoriser l'échec de la récupération afin d'être averti en cas de défaillance du DTC, comme dans l'exemple suivant.  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 1 -– presume commit  
GO  
reconfigure  
GO  
ALTER DATABASE pubs SET ONLINE –- run recovery again  
GO  
sp_configure 'in-doubt xact resolution', 0 –- back to no assumptions  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 L’option **in-doubt xact resolution** est une option avancée. Si vous utilisez la procédure stockée système **sp_configure** pour changer sa valeur, vous ne pouvez modifier l’option **in-doubt xact resolution** que si l’option **show advanced options** a la valeur 1. Le paramètre prend effet immédiatement (sans redémarrage du serveur).  
  
> [!NOTE]  
>  Une configuration identique de cette option dans toutes les instances de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impliquées dans les transactions distribuées permet d’éviter des incohérences dans les données.  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
