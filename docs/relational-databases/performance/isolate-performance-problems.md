---
title: Isoler les problèmes de performance | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- isolating performance problems [SQL Server]
- monitoring performance [SQL Server], isolating problems
- database monitoring [SQL Server], isolating problems
- tuning databases [SQL Server], isolating problems
- monitoring server performance [SQL Server], isolating problems
- database performance [SQL Server], isolating problems
- server performance [SQL Server], isolating problems
ms.assetid: 2eb425cb-9166-4027-ae08-c8fc2d236f44
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 643551201567ae10980c1fe3d5efca95a1bc9ded
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68051970"
---
# <a name="isolate-performance-problems"></a>Isoler les problèmes de performance
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Il est souvent plus efficace d’utiliser plusieurs outils [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Microsoft Windows ensemble pour isoler les problèmes de performance de base de données que d’utiliser un seul outil à la fois. Par exemple, la fonctionnalité graphique Plan d'exécution, également appelée plan d'exécution de requêtes, vous aide à reconnaître rapidement les blocages dans une seule requête. Toutefois, vous pouvez reconnaître d'autres problèmes de performance plus facilement si vous utilisez les fonctions de surveillance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de Windows en même temps.  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] permet de surveiller et de résoudre les problèmes liés à Transact-SQL et à l’application. Le Moniteur système permet de surveiller les problèmes liés au matériel ou à d'autres aspects du système.  
  
 Vous pouvez surveiller les éléments suivants pour résoudre les problèmes :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les traitements [!INCLUDE[tsql](../../includes/tsql-md.md)] envoyés par les applications des utilisateurs.  
  
-   L'activité de l'utilisateur, notamment les verrous de blocage et les blocages.  
  
-   L'activité matérielle, notamment l'utilisation du disque.  
  
 Vous pouvez identifier les problèmes suivants :  
  
-   des erreurs dans le développement d'une application liées à des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] mal rédigées ;  
  
-   des erreurs matérielles, notamment des erreurs de disque ou de réseau ;  
  
-   un blocage excessif dû à une base de données mal conçue.  
  
## <a name="tools-for-common-performance-problems"></a>Outils pour les problèmes de performance classiques  
 Il est très important aussi de sélectionner exactement le problème de performance que vous souhaitez faire surveiller ou régler par chaque outil. L'outil et l'utilitaire dépendent du type de problème de performance à résoudre.  
  
 Les rubriques suivantes décrivent différents outils de surveillance et de réglage et les problèmes correspondants.  
  
 [Identifier les goulots d’étranglement](../../relational-databases/performance/identify-bottlenecks.md)  
  
 [Surveiller l’utilisation de la mémoire](../../relational-databases/performance-monitor/monitor-memory-usage.md)  
  
  
