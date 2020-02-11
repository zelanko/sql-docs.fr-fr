---
title: remote admin connections (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- administrator connections [SQL Server]
- DAC
- connections [SQL Server], dedicated administrator
- remote admin connections option
- dedicated administrator connections [SQL Server]
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4e4894fa7e05c863095fdca7b26f448efe176216
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62781459"
---
# <a name="remote-admin-connections-server-configuration-option"></a>remote admin connections (option de configuration de serveur)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit une connexion administrateur dédiée. Celle-ci permet à un administrateur d’accéder à un serveur actif pour exécuter des fonctions de diagnostic ou des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ou pour résoudre des problèmes sur ce serveur, même s’il est verrouillé, que son état est anormal ou qu’il ne répond pas à une connexion du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Par défaut, cette connexion n'est disponible qu'à partir d'un client sur le serveur. Pour autoriser des applications clientes sur des ordinateurs distants à utiliser la connexion administrateur dédiée, utilisez l'option remote admin connections de sp_configure.  
  
 Par défaut, la connexion administrateur dédiée n'écoute que sur l'adresse IP (127.0.0.1), port 1434. Si le port TCP 1434 n’est pas disponible, un port TCP est affecté dynamiquement lors du démarrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Lorsque plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont installées sur un ordinateur, consultez le journal des erreurs afin de connaître le numéro de port TCP.  
  
 Le tableau suivant répertorie les valeurs possibles de l'option remote admin connections.  
  
|Valeur|Description|  
|-----------|-----------------|  
|0|Indique que seules les connexions locales sont autorisées à utiliser la connexion administrateur dédiée.|  
|1|Indique que les connexions à distance sont autorisées à utiliser la connexion administrateur dédiée.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant active la connexion administrateur dédiée à partir d'un ordinateur distant.  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion de diagnostic pour les administrateurs de base de données](diagnostic-connection-for-database-administrators.md)  
  
  
