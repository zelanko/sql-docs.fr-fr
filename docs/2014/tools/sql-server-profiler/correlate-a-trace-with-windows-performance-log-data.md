---
title: Mettre en corrélation une trace avec les données du journal de performances Windows | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- correlating trace with log data
- logs [SQL Server], traces
- Profiler [SQL Server Profiler], correlating trace with log data
- traces [SQL Server], logs
- SQL Server Profiler, correlating trace with log data
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3c8a3d7a9888423d312d578784e1f7e1ff75434d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63316310"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a>Mettre en corrélation une trace avec les données du journal de performances Windows
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]permet d'ouvrir un journal de performances Microsoft Windows, de choisir les compteurs que vous voulez corréler avec une trace et d'afficher les compteurs de performances sélectionnés en même temps que la trace dans l'interface utilisateur graphique du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . Lorsque vous sélectionnez un événement dans la fenêtre de trace, une barre verticale rouge dans le volet Moniteur système du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] indique les données du journal de performances en corrélation avec l'événement de trace sélectionné.  
  
 Pour mettre en corrélation une trace avec des compteurs de performances, ouvrez un fichier de trace ou une table qui contient les colonnes **StartTime** et **EndTime** data columns, et cliquez sur **Importer les données de performances** dans le menu [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **File**. Vous pouvez ouvrir un journal de performances et sélectionner les objets et compteurs du Moniteur système que vous voulez mettre en corrélation avec la trace.  
  
## <a name="see-also"></a>Voir aussi  
 [Corréler une trace aux données du journal de performances Windows &#40;SQL Server Profiler&#41;](correlate-a-trace-with-windows-performance-log-data.md)  
  
  
