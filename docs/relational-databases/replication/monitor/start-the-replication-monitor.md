---
title: "Démarrer le Moniteur de réplication | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e1a339c818c4199656d3114d214b2908501a017
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="start-the-replication-monitor"></a>Démarrer le Moniteur de réplication
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Vous pouvez démarrer le moniteur de réplication depuis [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] dans n'importe quelle instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ou à partir de l'invite de commandes. Après avoir démarré le Moniteur de réplication, ajoutez un ou plusieurs serveurs de publication à surveiller. Pour plus d’informations, consultez [Ajouter et supprimer des serveurs de publication à partir du moniteur de réplication](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md).  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a>Pour démarrer le moniteur de réplication à partir de SQL Server Management Studio  
  
1.  Connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Cliquez avec le bouton droit sur le dossier **Réplication** ou sur l'un de ses sous-dossiers, puis cliquez sur **Lancer le Moniteur de réplication**.  
  
### <a name="to-start-replication-monitor-from-the-command-prompt"></a>Pour démarrer le moniteur de réplication à partir de l'invite de commandes  
  
1.  À partir de l'invite de commandes, accédez au répertoire d'installation des outils. Le chemin d'accès par défaut est [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\.  
  
2.  Exécutez sqlmonitor.exe.  
  
## <a name="see-also"></a> Voir aussi  
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
