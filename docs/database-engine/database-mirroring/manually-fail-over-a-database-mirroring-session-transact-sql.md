---
title: "Basculer manuellement une session de mise en miroir de bases de données (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 085c7690a8185608e5e4af6253b53b726f53471e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="manually-fail-over-a-database-mirroring-session-transact-sql"></a>Basculer manuellement une session de mise en miroir de bases de données (Transact-SQL)
  Lorsque la base de données en miroir est synchronisée (que son état est SYNCHRONIZED), le propriétaire de la base de données peut initier un basculement manuel vers le serveur miroir. Le basculement manuel ne peut être lancé qu'à partir du serveur principal.  
  
### <a name="to-manually-fail-over-a-database-mirroring-session"></a>Pour basculer manuellement une session de mise en miroir de bases de données  
  
1.  Connectez-vous au serveur principal.  
  
2.  Définissez la base de données **master** comme contexte de la base de données :  
  
     **USE master;**  
  
3.  Exécutez l'instruction suivante sur le serveur principal :  
  
     [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md) *nom_base_de_données* SET PARTNER FAILOVER, où *nom_base_de_données* est la base de données mise en miroir.  
  
     Cela lance une transition immédiate du serveur miroir vers le rôle de principal.  
  
 Sur l'ancien principal, les clients sont déconnectés de la base de données et les transactions en cours sont restaurées.  
  
> [!NOTE]  
>  Les transactions qui ont été préparées à l'aide du service MSDTC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator) mais qui ne sont toujours pas validées au moment du basculement, sont considérés abandonnées après le basculement de la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [Basculer manuellement une session de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)   
 [Basculement de rôle durant une session de mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  
