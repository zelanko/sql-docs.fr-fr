---
title: server trigger recursion (option de configuration de serveur) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e8f9412d311c5c12d0a77eb4ec0fb02fb9664d75
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="server-trigger-recursion-server-configuration-option"></a>server trigger recursion (Option de configuration de serveur)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option **server trigger recursion** pour permettre ou non l’exécution de manière récursive des déclencheurs au niveau du serveur. Lorsque cette option a la valeur 1 (ON), les déclencheurs au niveau du serveur peuvent être exécutés de manière récursive. Lorsqu'elle a la valeur 0 (OFF), les déclencheurs ne peuvent pas être exécutés de manière récursive. Seule la récursivité directe est désactivée lorsque l'option server trigger recursion a la valeur 0 (OFF). (Pour désactiver la récursivité indirecte, affectez à l’option **nested triggers** la valeur 0.) La valeur par défaut de cette option est 1 (ON). Le paramètre prend effet immédiatement (sans redémarrage du serveur).  
  
 Pour plus d’informations, consultez [Créer des déclencheurs imbriqués](../../relational-databases/triggers/create-nested-triggers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
