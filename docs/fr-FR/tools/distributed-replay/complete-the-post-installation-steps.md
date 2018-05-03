---
title: Effectuez les étapes de post-installation | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: distributed-replay
ms.reviewer: ''
ms.suite: sql
ms.technology:
- setup-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 397cb416c9c59482cf97be8e7554f5f2af7c2d7a
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="complete-the-post-installation-steps"></a>Suivre les étapes consécutives à l'installation
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Après avoir installé Distributed Replay, vous devez modifier le compte Distributed Replay Controller et les comptes de services clients.  
  
### <a name="to-complete-the-post-installation-steps"></a>Pour suivre les étapes consécutives à l'installation  
  
1.  **Créez des règles de pare-feu**: sur les ordinateurs contrôleurs et clients, vous devez autoriser le trafic entrant à travers le pare-feu pour le service correspondant. Spécifiez des règles de pare-feu pour les exécutables du service, situés dans les dossiers d'installation.  
  
    1.  Pour le service contrôleur, créez une règle pour **DReplayController.exe**, situé dans le dossier d’installation. Par exemple, la commande suivante active cette règle, sachant que `%InstallPath%` est le dossier d'installation du service :  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  Pour le service client, sur chaque ordinateur client, créez une règle pour **DReplayClient.exe**, situé dans le dossier d’installation. Par exemple, la commande suivante active cette règle, sachant que `%InstallPath%` est le dossier d'installation du service :  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **Accordez à chaque client des autorisations sur le serveur cible**: après avoir achevé l’installation du service client sur les ordinateurs clients, vous devez ajouter manuellement les comptes de services clients au rôle sysadmin sur l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Vous devez posséder des autorisations administratives pour installer les fonctionnalités de Distributed Replay. Seule une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disposant d’autorisations sysadmin peut ajouter des comptes de services clients au rôle serveur sysadmin du serveur de test. Pour plus d'informations sur les questions de sécurité de Distributed Replay, consultez [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
  
