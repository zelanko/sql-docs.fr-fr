---
title: "Changer la sécurité des transactions dans une session de mise en miroir de bases de données (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
caps.latest.revision: 38
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9cf22d160c37c4d8904830d363e6358cb5b40aea
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="change-transaction-safety-in-a-database-mirroring-session-transact-sql"></a>Modifier la sécurité des transactions dans une session de mise en miroir de bases de données (Transact-SQL)
  La sécurité des transactions est l'attribut qui contrôle le mode de fonctionnement de la session. Le propriétaire de la base de données peut toutefois modifier à tout moment la sécurité des transactions. Par défaut, le niveau de sécurité est FULL (mode synchrone).  
  
 La désactivation de la sécurité des transactions fait passer la session en mode asynchrone, ce qui optimise les performances. Si l'instance principale devient non disponible, le miroir s'arrête mais reste accessible en tant que secours semi-automatique (le basculement impose un service forcé avec une possibilité de perte de données).  
  
### <a name="to-turn-on-transaction-safety"></a>Pour activer la sécurité des transactions  
  
1.  Connectez-vous au serveur principal.  
  
2.  Émettez l'instruction Transact-SQL suivante :  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY FULL  
    ```  
  
     où *\<database>* est le nom de la base de données mise en miroir.  
  
### <a name="to-turn-off-transaction-safety"></a>Pour désactiver la sécurité des transactions  
  
1.  Connectez-vous au serveur principal.  
  
2.  Émettez l'instruction suivante :  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY OFF  
    ```  
  
     où *\<database>* est la base de données mise en miroir.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [Modes de fonctionnement de la mise en miroir de bases de données](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)  
  
  

