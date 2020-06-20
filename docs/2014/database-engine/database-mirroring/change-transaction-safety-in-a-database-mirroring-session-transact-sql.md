---
title: Changer la sécurité des transactions dans une session de mise en miroir de bases de données (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d8bc9d0fb639770d33507c29a6ec67f60bd0434a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934393"
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
 [Mise en miroir de bases de données ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Modes de fonctionnement de la mise en miroir de bases de données](database-mirroring-operating-modes.md)  
  
  
