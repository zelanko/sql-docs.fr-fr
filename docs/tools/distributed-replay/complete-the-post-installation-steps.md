---
title: Suivre les étapes consécutives à l'installation
titleSuffix: SQL Server Distributed Replay
description: Après avoir installé Distributed Replay, vous devez modifier les comptes de service Distributed Replay Controller et Distributed Replay Client.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
author: MikeRayMSFT
ms.author: mikeray
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: e38755c65e457123c732035a2874f9904644e0d5
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2020
ms.locfileid: "83001169"
---
# <a name="complete-the-post-installation-steps"></a>Suivre les étapes consécutives à l'installation

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Après avoir installé Distributed Replay, vous devez modifier le compte de contrôleur Distributed Replay et les comptes de services clients.  
  
## <a name="to-complete-the-post-installation-steps"></a>Pour suivre les étapes consécutives à l'installation  
  
1. **Créez des règles de pare-feu** : Sur les ordinateurs contrôleurs et clients, vous devez autoriser le trafic entrant à travers le pare-feu pour le service correspondant. Spécifiez des règles de pare-feu pour les exécutables du service, situés dans les dossiers d'installation.  
  
    1. Pour le service contrôleur, créez une règle pour **DReplayController.exe**, situé dans le dossier d’installation. Par exemple, la commande suivante active cette règle, sachant que `%InstallPath%` est le dossier d'installation du service :  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2. Pour le service client, sur chaque ordinateur client, créez une règle pour **DReplayClient.exe**, situé dans le dossier d’installation. Par exemple, la commande suivante active cette règle, sachant que `%InstallPath%` est le dossier d'installation du service :  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2. **Accorder à chaque client des autorisations sur le serveur cible** : Après avoir achevé l’installation du service client sur les ordinateurs clients, vous devez ajouter manuellement les comptes de services clients au rôle sysadmin sur l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework

Vous devez posséder des autorisations administratives pour installer les fonctionnalités de Distributed Replay. Seule une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disposant d’autorisations sysadmin peut ajouter des comptes de services clients au rôle serveur sysadmin du serveur de test. Pour plus d'informations sur les questions de sécurité de Distributed Replay, consultez [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).