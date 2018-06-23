---
title: Démarrer le moniteur de mise en miroir de bases de données (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- monitoring database mirroring [SQL Server]
- Database Mirroring Monitor [SQL Server], starting
- database mirroring [SQL Server], monitoring
ms.assetid: 53165335-97ca-4f88-8e78-22f1839dee98
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 78dd47f2adc268418a3cfd213d31214b36f77205
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143098"
---
# <a name="start-database-mirroring-monitor-sql-server-management-studio"></a>Démarrer le moniteur de mise en miroir de bases de données (SQL Server Management Studio)
  Le moniteur de mise en miroir de base de données fait partie du Moniteur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , que vous pouvez démarrer à partir de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!NOTE]  
>  Le Moniteur de mise en miroir de bases de données n’est pas disponible dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
### <a name="to-launch-the-database-mirroring-monitor"></a>Pour lancer l'analyse de mise en miroir de base de données  
  
1.  Après vous être connecté à l'instance du serveur principal, dans l'Explorateur d'objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Bases de données**, puis sélectionnez la base de données à analyser.  
  
3.  Cliquez avec le bouton droit sur la base de données, sélectionnez **Tâches**, puis cliquez sur **Lancer le moniteur de mise en miroir de bases de données**.  
  
4.  Dans la boîte de dialogue **Moniteur de mise en miroir de bases de données** , cliquez sur **Inscrire la base de données mise en miroir** pour inscrire une ou plusieurs bases de données en miroir.  
  
    > [!NOTE]  
    >  Lorsque vous inscrivez une base de données sur un partenaire, elle est automatiquement inscrite sur l'autre partenaire. Si le moniteur possède déjà des informations d'identification de connexion pour l'instance de l'autre partenaire, elles sont utilisées pour établir la connexion. Autrement, le moniteur tente d'établir une connexion avec l'authentification Windows. Si vous souhaitez modifier les informations d’identification utilisées pour la connexion à l’une des instances de serveur, cliquez sur **Afficher la boîte de dialogue Gérer les connexions serveur lorsque je clique sur OK**.  
  
 Pour plus d’informations sur le moniteur de mise en miroir de bases de données, consultez [Vue d’ensemble du moniteur de mise en miroir de bases de données](database-mirroring-monitor-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
  