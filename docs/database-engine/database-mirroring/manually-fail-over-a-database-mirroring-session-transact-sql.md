---
title: "Basculer manuellement une session de mise en miroir de bases de donn&#233;es (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "basculement [SQL Server], mise en miroir de bases de données"
  - "basculement manuel [SQL Server]"
  - "mise en miroir de bases de données [SQL Server], basculement"
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
caps.latest.revision: 32
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 32
---
# Basculer manuellement une session de mise en miroir de bases de donn&#233;es (Transact-SQL)
  Lorsque la base de données en miroir est synchronisée (que son état est SYNCHRONIZED), le propriétaire de la base de données peut initier un basculement manuel vers le serveur miroir. Le basculement manuel ne peut être lancé qu'à partir du serveur principal.  
  
### Pour basculer manuellement une session de mise en miroir de bases de données  
  
1.  Connectez-vous au serveur principal.  
  
2.  Définissez la base de données **master** comme contexte de la base de données :  
  
     **USE master;**  
  
3.  Exécutez l'instruction suivante sur le serveur principal :  
  
     [ALTER DATABASE](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md) *nom_base_de_données* SET PARTNER FAILOVER, où *nom_base_de_données* est la base de données mise en miroir.  
  
     Cela lance une transition immédiate du serveur miroir vers le rôle de principal.  
  
 Sur l'ancien principal, les clients sont déconnectés de la base de données et les transactions en cours sont restaurées.  
  
> [!NOTE]  
>  Les transactions qui ont été préparées à l'aide du service MSDTC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator) mais qui ne sont toujours pas validées au moment du basculement, sont considérés abandonnées après le basculement de la base de données.  
  
## Voir aussi  
 [Mise en miroir de bases de données ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [Basculer manuellement une session de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)   
 [Basculement de rôle durant une session de mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  