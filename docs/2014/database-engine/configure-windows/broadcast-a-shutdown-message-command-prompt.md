---
title: Diffuser un message d’arrêt (invite de commandes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, stopping
- named instances [SQL Server], broadcasting shutdown messages
- shutdown message broadcast
- broadcasting shutdown message
- command prompt [SQL Server], broadcasting shutdown messages
- default instances [SQL Server], broadcasting shutdown messages
- stopping SQL Server
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5349f45891dbca2c9135c38c1976f71c87491212
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62786653"
---
# <a name="broadcast-a-shutdown-message-command-prompt"></a>Diffuser un message d'arrêt (invite de commandes)
  Cette rubrique décrit comment diffuser un message d’arrêt dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de la commande **net send** . Dans ce message, incluez l'heure d'arrêt de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre aux utilisateurs de terminer leurs tâches.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-broadcast-a-shutdown-message"></a>Pour diffuser un message d'arrêt  
  
1.  À partir d'une invite de commandes, entrez :  
  
     **net send /users "message"**  
  
     L’option **/users** spécifie que le message doit être envoyé à tous les utilisateurs connectés au serveur.  
  
> [!NOTE]  
>  Pour que la commande **net send** fonctionne, le service Affichage des messages doit être exécuté sur l’ordinateur émetteur et sur les ordinateurs récepteurs. Le service Affichage des messages est désactivé par défaut dans Windows Server 2003. Pour plus d’informations sur **net send**, consultez la documentation de Windows.  
  
 Sur votre réseau, il peut être préférable de contacter les utilisateurs par courrier électronique ou par téléphone. Pour savoir quels sont les utilisateurs actuellement connectés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilisez le Moniteur d'activité. Pour plus d’informations sur le moniteur d’activité, consultez [Moniteur d’activité](../../relational-databases/performance-monitor/activity-monitor.md) et [Ouvrir le Moniteur d’activité &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
