---
title: "Effectuez les étapes de post-installation | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
caps.latest.revision: "8"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 13be47f21e5d4be72747ccec82d1a991d3d38de7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="complete-the-post-installation-steps"></a>Suivre les étapes consécutives à l'installation
  Après avoir installé Distributed Replay, vous devez modifier le compte de contrôleur Distributed Replay et les comptes de services clients.  
  
### <a name="to-complete-the-post-installation-steps"></a>Pour suivre les étapes consécutives à l'installation  
  
1.  **Créez des règles de pare-feu**: sur les ordinateurs contrôleurs et clients, vous devez autoriser le trafic entrant à travers le pare-feu pour le service correspondant. Spécifiez des règles de pare-feu pour les exécutables du service, situés dans les dossiers d'installation.  
  
    1.  Pour le service contrôleur, créez une règle pour **DReplayController.exe**, situé dans le dossier d’installation. Par exemple, la commande suivante active cette règle, sachant que `%InstallPath%` est le dossier d'installation du service :  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  Pour le service client, sur chaque ordinateur client, créez une règle pour **DReplayClient.exe**, situé dans le dossier d’installation. Par exemple, la commande suivante active cette règle, sachant que `%InstallPath%` est le dossier d'installation du service :  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **Accordez à chaque client des autorisations sur le serveur cible**: après avoir achevé l’installation du service client sur les ordinateurs clients, vous devez ajouter manuellement les comptes de services clients au rôle sysadmin sur l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Vous devez posséder des autorisations administratives pour installer les fonctionnalités de Distributed Replay. Seule une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disposant d’autorisations sysadmin peut ajouter des comptes de services clients au rôle serveur sysadmin du serveur de test. Pour plus d'informations sur les questions de sécurité de Distributed Replay, consultez [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
  
