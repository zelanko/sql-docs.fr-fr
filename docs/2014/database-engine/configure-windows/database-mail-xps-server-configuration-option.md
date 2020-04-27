---
title: Database Mail XPs (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e916fe3b76abfa8773a757cf2779e7d5cbf26b86
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62810541"
---
# <a name="database-mail-xps-server-configuration-option"></a>Database Mail XPs (option de configuration de serveur)
  Utilisez **l’option** pour activer la messagerie de base de données sur ce serveur. Les valeurs possibles sont les suivantes :  
  
-   **0** indique que la messagerie de base de données n’est pas disponible (valeur par défaut).  
  
-   **1** indique que la messagerie de base de données est disponible.  
  
 Le paramètre prend effet immédiatement, sans arrêt et redémarrage du serveur.  
  
 Après avoir activé la messagerie de base de données, vous devez configurer une base de données hôte afin qu'elle utilise la messagerie de base de données.  
  
 La configuration de la messagerie de base de données à l’aide de l’ **Assistant Configuration de la messagerie de base de données** active les procédures stockées étendues de la messagerie de base de données dans la base de données **msdb** . Si vous utilisez l’ **Assistant Configuration de la messagerie de base de données**, il n’est pas nécessaire d’utiliser l’exemple **sp_configure** ci-dessous.  
  
 Si l’option **Database Mail XPs** a la valeur 0, la messagerie de base de données ne démarre pas. Si elle est en cours d’exécution lorsque la valeur 0 est affectée à l’option, elle continue de s’exécuter et d’envoyer des messages jusqu’à ce qu’elle soit inactive pendant la durée configurée dans l’option **DatabaseMailExeMinimumLifeTime** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant active les procédures stockées étendues de la messagerie de base de données.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)  
  
  
