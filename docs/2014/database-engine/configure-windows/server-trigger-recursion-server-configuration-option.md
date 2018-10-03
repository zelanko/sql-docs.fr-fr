---
title: server trigger recursion (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1c2e8192c83fe0a654d90b47edaa5d77eb4c483f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112031"
---
# <a name="server-trigger-recursion-server-configuration-option"></a>server trigger recursion (Option de configuration de serveur)
  Utilisez l’option **server trigger recursion** pour permettre ou non l’exécution de manière récursive des déclencheurs au niveau du serveur. Lorsque cette option a la valeur 1 (ON), les déclencheurs au niveau du serveur peuvent être exécutés de manière récursive. Lorsqu'elle a la valeur 0 (OFF), les déclencheurs ne peuvent pas être exécutés de manière récursive. Seule la récursivité directe est désactivée lorsque l'option server trigger recursion a la valeur 0 (OFF). (Pour désactiver la récursivité indirecte, affectez à l’option **nested triggers** la valeur 0.) La valeur par défaut de cette option est 1 (ON). Le paramètre prend effet immédiatement (sans redémarrage du serveur).  
  
 Pour plus d’informations, consultez [Créer des déclencheurs imbriqués](../../relational-databases/triggers/create-nested-triggers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
