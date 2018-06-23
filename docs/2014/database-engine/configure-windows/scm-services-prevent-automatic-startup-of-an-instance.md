---
title: Empêcher le démarrage automatique d’une Instance de SQL Server (Gestionnaire de Configuration SQL Server) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, stopping
- SQL Server, automatic startup
- canceling automatic startup
- stopping SQL Server
- preventing automatic startups [SQL Server]
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
caps.latest.revision: 33
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b21ac71b54c9bfee76079f86c1d6d1a32fc0f9dc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041172"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a>Empêcher le démarrage automatique d'une instance de SQL Server (Gestionnaire de configuration SQL Server)
  Cette rubrique décrit comment empêcher une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de démarrer automatiquement dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration SQL Server. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en principe configuré afin de démarrer automatiquement. Vous pouvez modifier ce comportement en définissant le mode de démarrage de l'instance sur Manuel.  
  
##  <a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a>Pour empêcher le démarrage automatique d'une instance de SQL Server  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
2.  Dans le Gestionnaire de configuration SQL Server, développez **Services**, puis cliquez sur **SQL Server**.  
  
3.  Dans le volet d’informations, cliquez avec le bouton droit sur **MSSQLServer**, puis cliquez sur **Propriétés**.  
  
4.  Dans le **SQL Server \< ***instancename***> Propriétés** boîte de dialogue le **propriétés** , définissez la valeur de **le Mode de démarrage**à **manuel**.  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés de SQL Server \<***nom_instance***>**, puis fermez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser](start-stop-pause-resume-restart-sql-server-services.md)  
  
  