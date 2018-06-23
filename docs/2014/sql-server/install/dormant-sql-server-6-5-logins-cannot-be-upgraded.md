---
title: Les connexions SQL Server 6.5 dormantes ne peuvent pas être mis à niveau | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7bf1bc14deea80f60692b9b25cc1f119ac69d307
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152481"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a>Les connexions SQL Server 6.5 dormantes ne peuvent pas être mises à niveau
  Le Conseiller de mise à niveau a détecté un nom de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dont le mot de passe ne peut pas être directement mis à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Pour activer cette connexion, vous devez redéfinir le mot de passe. Vous pouvez redéfinir le mot de passe en utilisant ALTER LOGIN.  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 Le nouveau mot de passe sera validé par rapport à la stratégie de complexité des mots de passe de votre système, sauf si la vérification de la stratégie est désactivée. Nous vous recommandons d'utiliser des mots de passe complexes et de ne pas désactiver la vérification de la stratégie. L'option MUST_CHANGE oblige l'utilisateur à choisir un nouveau mot de passe. Cette étape est recommandée, mais elle n’est pas obligatoire.  
  
 Vous pouvez identifier les connexions dormantes à l'aide de la requête suivante :  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
