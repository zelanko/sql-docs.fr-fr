---
title: Création d’une chaîne de connexion valide avec le protocole de mémoire partagée | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], shared memory
- aliases [SQL Server], shared memory
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 2a022783fb1810ed94f5830ad898dca430fe5236
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67732745"
---
# <a name="creating-a-valid-connection-string-using-shared-memory-protocol"></a>Création d'une chaîne de connexion valide à l'aide du protocole de mémoire partagée
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Les connexions à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un client exécuté sur le même ordinateur utilisent le protocole de mémoire partagée. La mémoire partagée ne possède aucune propriété configurable. La mémoire partagée est toujours sollicitée en premier et ne peut pas être déplacée depuis sa position initiale dans la liste des **Protocoles activés** dans la boite de dialogue de **Propriétés de protocoles clients** . Le protocole de mémoire partagée peut être désactivé, ce qui est utile lors du dépannage de l'un des autres protocoles.  
  
 Vous ne pouvez pas créer un alias utilisant le protocole de mémoire partagée mais, si la mémoire partagée est activée, la connexion au [!INCLUDE[ssDE](../../includes/ssde-md.md)] à partir du nom crée une connexion de mémoire partagée. Une chaîne de connexion de mémoire partagée utilise le format `lpc:<servername>[\instancename]`.  
  
## <a name="connecting-to-the-local-server"></a>Connexion au serveur local  
 Quand vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alors que celui-ci s’exécute sur le même ordinateur que l’ordinateur client, vous pouvez utiliser **(local)** comme nom de serveur. Cette option n'est pas conseillée dans la mesure où elle est source d'ambiguïté ; toutefois, elle peut s'avérer utile lorsqu'il est certain que le client s'exécute sur l'ordinateur visé. Par exemple, quand vous créez une application pour des utilisateurs itinérants déconnectés, tels que des commerciaux, où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute sur des ordinateurs portables et stocke les données de projet, un client qui se connecte à **(local)** se connecte toujours à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécutant sur l’ordinateur portable. Vous pouvez utiliser le mot **localhost** ou un point ( **.** ) à la place de **(local)** .  
  
## <a name="verifying-your-connection-protocol"></a>Vérification du protocole de connexion  
 La requête suivante retournera le protocole utilisé pour la connexion active.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>Exemples :  
 Les noms suivants permettent d'établir une connexion à l'ordinateur local avec le protocole de mémoire partagée si celui-ci est activé :  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 Vous ne pouvez pas créer un alias pour une connexion de mémoire partagée.  
  
> [!NOTE]  
>  La spécification d’une adresse IP dans la zone **Serveur** génère une connexion TCP/IP.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une chaîne de connexion valide à l’aide du protocole TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Création d’une chaîne de connexion valide avec des canaux nommés](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)   
 [Choix d'un protocole réseau](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
