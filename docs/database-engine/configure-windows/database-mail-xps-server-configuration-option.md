---
title: Database Mail XPs (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e16286e558d860a346ba8fff366009f064e65f91
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68011960"
---
# <a name="database-mail-xps-server-configuration-option"></a>Database Mail XPs (option de configuration de serveur)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Utilisez **l’option** pour activer la messagerie de base de données sur ce serveur. Les valeurs possibles sont les suivantes :  
  
- `0`: Database Mail n’est pas disponible (par défaut).  
  
- `1`: Database Mail est disponible.  
  
 Le paramètre prend effet immédiatement, sans arrêt et redémarrage du serveur.  
  
 Après avoir activé la messagerie de base de données, vous devez configurer une base de données hôte afin qu'elle utilise la messagerie de base de données.  
  
 La configuration de Database Mail à l’aide de l’**Assistant Configuration de Database Mail** active les procédures stockées étendues de la messagerie de base de données dans la base de données `msdb`. Si vous utilisez l’**Assistant Configuration de Database Mail**, il n’est pas nécessaire d’utiliser l’exemple `sp_configure` ci-dessous.  
  
 Si l’option **Database Mail XPs** a la valeur `0`, Database Mail ne démarre pas. Si elle est en cours d’exécution lorsque la valeur `0` est affectée à l’option, elle continue de s’exécuter et d’envoyer des messages jusqu’à ce qu’elle soit inactive pendant la durée configurée dans l’option `DatabaseMailExeMinimumLifeTime`.  
  
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

L’exemple suivant active les procédures stockées étendues de Database Mail, si celles-ci ne le sont pas déjà.

```sql
IF EXISTS (
    SELECT 1 FROM sys.configurations 
    WHERE NAME = 'Database Mail XPs' AND VALUE = 0)
BEGIN
  PRINT 'Enabling Database Mail XPs'
  EXEC sp_configure 'show advanced options', 1;  
  RECONFIGURE
  EXEC sp_configure 'Database Mail XPs', 1;  
  RECONFIGURE  
END
```

## <a name="see-also"></a>Voir aussi
[Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)  
