---
title: server trigger recursion (option de configuration de serveur) | Microsoft Docs
description: Découvrez comment l’option « Récursivité des déclencheurs du serveur » affecte la récursivité dans les déclencheurs au niveau du serveur SQL Server. Découvrez comment activer et désactiver la récursivité directe et indirecte.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7dc2dcd132ef32ba4f026a1a9b76d4e67df28b26
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715560"
---
# <a name="server-trigger-recursion-server-configuration-option"></a>server trigger recursion (Option de configuration de serveur)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Utilisez l’option **server trigger recursion** pour permettre ou non l’exécution de manière récursive des déclencheurs au niveau du serveur. Lorsque cette option a la valeur 1 (ON), les déclencheurs au niveau du serveur peuvent être exécutés de manière récursive. Lorsqu'elle a la valeur 0 (OFF), les déclencheurs ne peuvent pas être exécutés de manière récursive. Seule la récursivité directe est désactivée lorsque l'option server trigger recursion a la valeur 0 (OFF). (Pour désactiver la récursivité indirecte, affectez à l’option **nested triggers** la valeur 0.) La valeur par défaut de cette option est 1 (ON). Le paramètre prend effet immédiatement (sans redémarrage du serveur).  
  
 Pour plus d’informations, consultez [Créer des déclencheurs imbriqués](../../relational-databases/triggers/create-nested-triggers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
