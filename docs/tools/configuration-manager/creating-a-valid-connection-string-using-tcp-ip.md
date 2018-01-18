---
title: "Création d’une chaîne de connexion valide à l’aide de TCP IP | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection strings [Database Engine]
- ports [SQL Server], connecting to
- TCP/IP [SQL Server], connection strings
- connection strings [Database Engine], TCP/IP
- aliases [SQL Server], TCP/IP
ms.assetid: ee5dbc2c-1fc6-42bd-bdf5-efa792557934
caps.latest.revision: "31"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 462427bd676d23a3a490d6c04b87c71a716c3a5c
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="creating-a-valid-connection-string-using-tcp-ip"></a>Création d’une chaîne de connexion valide à l’aide du protocole TCP/IP
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Pour créer une chaîne de connexion valide à l’aide de TCP/IP, procédez comme suit :  
  
-   Spécifiez un **nom de l'alias**.  
  
-   Pour **Serveur**, entrez le nom d’un serveur auquel vous pouvez vous connecter à l’aide de l’utilitaire **PING** , ou une adresse IP à laquelle vous pouvez vous connecter au moyen de l’utilitaire **PING** . Pour une instance nommée, ajoutez le nom de l'instance.  
  
-   Spécifiez **TCP/IP** comme **Protocole**.  
  
-   Vous pouvez éventuellement entrer un numéro de port dans **Numéro de port**. La valeur par défaut est 1433 ; il s'agit du numéro de port de l'instance par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)] sur un serveur. Pour vous connecter à une instance nommée ou à une instance par défaut qui n'est pas à l'écoute sur le port 1433, vous devez spécifier le numéro de port ou démarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser. Pour plus d’informations sur la configuration du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, consultez [Service SQL Server Browser](../../tools/configuration-manager/sql-server-browser-service.md).  
  
 Au moment de la connexion, le composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client lit dans le Registre les valeurs de serveur, protocole et port pour le nom d'alias spécifié, et crée une chaîne de connexion au format `tcp:<servername>[\<instancename>],<port>` ou `tcp:<IPAddress>[\<instancename>],<port>`.  
  
> [!NOTE]  
>  Le pare-feu [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ferme le port 1433 par défaut. Étant donné que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] communique via le port 1433, vous devez rouvrir le port si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour écouter les connexions clientes entrantes utilisant TCP/IP. Pour plus d'informations sur la configuration d'un pare-feu, consultez « Procédure : configurer un pare-feu pour accéder à SQL Server » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou passez en revue la documentation de votre pare-feu.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend entièrement en charge le protocole Internet version 4 (IPv4) et le protocole Internet version 6 (IPv6). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Gestionnaire de configuration accepte à la fois IPv4 et IPv6 formats pour les adresses IP. Pour plus d'informations sur IPv6, consultez « Connexion avec IPv6 » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="connecting-to-the-local-server"></a>Connexion au serveur local  
 Lorsque vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alors que celui-ci est exécuté sur le même ordinateur que l'ordinateur client, vous pouvez utiliser `(local)` comme nom de serveur. Cette option n'est pas conseillée dans la mesure où elle est source d'ambiguïté ; toutefois, elle peut s'avérer utile lorsqu'il est certain que le client s'exécute sur l'ordinateur visé. Par exemple, lorsque vous créez une application destinée à des utilisateurs itinérants déconnectés, tels que des vendeurs, pour lesquels [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute sur des ordinateurs portables et stocke les données de projet, un client établissant une connexion à `(local)` se connecte toujours à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cours d'exécution sur l'ordinateur portable. Vous pouvez utiliser le mot `localhost` ou un point (**.**) à la place de `(local)`.  
  
## <a name="verifying-your-connection-protocol"></a>Vérification de votre protocole de connexion  
 La requête suivante retourne le protocole utilisé pour la connexion active.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>Exemples  
 Connexion à partir du nom de serveur :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 Connexion à une instance nommée à partir du nom de serveur :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>\<instancename>  
  
```  
  
 Connexion à un port spécifié à partir du nom de serveur :  
  
```  
Alias Name         <serveralias>  
Port No            <port>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 Connexion par l'adresse IP :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 Connexion par l'adresse IP à une instance nommée :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>\<instancename>  
  
```  
  
 Connexion par l'adresse IP à un port spécifié :  
  
```  
Alias Name         <serveralias>  
Port No            <port number>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 Connexion à l'ordinateur local à l'aide du paramètre `(local)`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             (local)  
  
```  
  
 Connexion à l'ordinateur local à l'aide du paramètre `localhost`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost  
  
```  
  
 Connexion à une instance nommée sur l'ordinateur local `localhost`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost\<instancename>  
  
```  
  
 Connexion à l'ordinateur local à l'aide d'un point :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .  
  
```  
  
 Connexion à une instance nommée sur l'ordinateur local à l'aide d'un point :  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .\<instancename>  
  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur la spécification du protocole réseau en tant que paramètre **sqlcmd** , consultez « Procédure : établir une connexion au moteur de base de données à l’aide de sqlcmd.exe » dans la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une chaîne de connexion valide à l’aide du protocole de mémoire partagée](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)   
 [Création d’une chaîne de connexion valide à l’aide de canaux nommés](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)   
 [Choix d’un protocole réseau](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
