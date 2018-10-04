---
title: Démarrage de SQL Server avec une configuration minimale | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 146682e4de1e74359bef52e0de6860dcabe8b0c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150619"
---
# <a name="start-sql-server-with-minimal-configuration"></a>Démarrage de SQL Server avec une configuration minimale
  Si vous rencontrez des problèmes de configuration qui empêchent le démarrage du serveur, vous pouvez démarrer une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’option de démarrage en configuration minimale. Il s’agit de l’option de démarrage **-f**. Le démarrage d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server avec une configuration minimale fait automatiquement passer le serveur en mode mono-utilisateur.  
  
 Lorsque vous démarrez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode configuration minimale, notez les éléments suivants :  
  
-   un seul utilisateur peut se connecter, tandis que le processus CHECKPOINT n'est pas exécuté ;  
  
-   l'accès à distance et la lecture anticipée sont désactivés ;  
  
-   les procédures stockées de démarrage ne sont pas exécutées.  
  
 N'oubliez pas ensuite de revenir à l'option de démarrage appropriée, d'arrêter le serveur, puis de le redémarrer.  
  
> [!IMPORTANT]  
>  Utilisez l’utilitaire **sqlcmd** et la connexion administrateur dédiée (DAC) pour vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous utilisez une connexion par défaut, arrêtez le service SQL Server Agent avant de vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode de configuration minimale. Sinon, le service SQL Server Agent utilise la connexion et bloque votre connexion à SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer, arrêter ou suspendre le service SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)   
 [Connexion de diagnostic pour les administrateurs de base de données](diagnostic-connection-for-database-administrators.md)   
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Options de démarrage du service moteur de base de données](database-engine-service-startup-options.md)  
  
  
