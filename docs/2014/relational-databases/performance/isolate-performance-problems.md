---
title: Isoler les problèmes de performance | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e700f5178a3520fe83f4d896662a8741aa166b9a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63150909"
---
# <a name="isolate-performance-problems"></a>Isoler les problèmes de performance
  Il est souvent plus efficace d’utiliser plusieurs [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] outils ou Microsoft Windows conjointement pour isoler les problèmes de performances de la base de données que d’utiliser un seul outil à la fois. Par exemple, la fonctionnalité graphique Plan d'exécution, également appelée plan d'exécution de requêtes, vous aide à reconnaître rapidement les blocages dans une seule requête. Toutefois, vous pouvez reconnaître d'autres problèmes de performance plus facilement si vous utilisez les fonctions de surveillance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de Windows en même temps.  
  
 
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] permet de surveiller et de résoudre les problèmes liés à Transact-SQL et à l’application. Le Moniteur système permet de surveiller les problèmes liés au matériel ou à d'autres aspects du système.  
  
 Vous pouvez surveiller les éléments suivants pour résoudre les problèmes :  
  
-   
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les traitements [!INCLUDE[tsql](../../includes/tsql-md.md)] envoyés par les applications des utilisateurs.  
  
-   L'activité de l'utilisateur, notamment les verrous de blocage et les blocages.  
  
-   L'activité matérielle, notamment l'utilisation du disque.  
  
 Vous pouvez identifier les problèmes suivants :  
  
-   des erreurs dans le développement d'une application liées à des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] mal rédigées ;  
  
-   des erreurs matérielles, notamment des erreurs de disque ou de réseau ;  
  
-   un blocage excessif dû à une base de données mal conçue.  
  
## <a name="tools-for-common-performance-problems"></a>Outils pour les problèmes de performance classiques  
 Il est très important aussi de sélectionner exactement le problème de performance que vous souhaitez faire surveiller ou régler par chaque outil. L'outil et l'utilitaire dépendent du type de problème de performance à résoudre.  
  
 Les rubriques suivantes décrivent différents outils de surveillance et de réglage et les problèmes correspondants.  
  
 [Identifier les goulots d'étranglement](identify-bottlenecks.md)  
  
 [Surveiller l’utilisation de la mémoire](../performance-monitor/monitor-memory-usage.md)  
  
  
