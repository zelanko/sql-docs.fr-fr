---
title: Mettre en corrélation une trace avec les données du journal de performances Windows | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- correlating trace with log data
- logs [SQL Server], traces
- Profiler [SQL Server Profiler], correlating trace with log data
- traces [SQL Server], logs
- SQL Server Profiler, correlating trace with log data
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3918c8b5f92aa7d77c50cfe43e97d15413ceb1f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038974"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a>Mettre en corrélation une trace avec les données du journal de performances Windows
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]permet d'ouvrir un journal de performances Microsoft Windows, de choisir les compteurs que vous voulez corréler avec une trace et d'afficher les compteurs de performances sélectionnés en même temps que la trace dans l'interface utilisateur graphique du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . Lorsque vous sélectionnez un événement dans la fenêtre de trace, une barre verticale rouge dans le volet Moniteur système du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] indique les données du journal de performances en corrélation avec l'événement de trace sélectionné.  
  
 Pour mettre en corrélation une trace avec des compteurs de performances, ouvrez un fichier de trace ou une table qui contient les colonnes **StartTime** et **EndTime** data columns, et then click **Importer les données de performances** dans le menu [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **File** menu. Vous pouvez ouvrir un journal de performances et sélectionner les objets et compteurs du Moniteur système que vous voulez mettre en corrélation avec la trace.  
  
## <a name="see-also"></a>Voir aussi  
 [Corréler une trace aux données du journal de performances Windows &#40;SQL Server Profiler&#41;](correlate-a-trace-with-windows-performance-log-data.md)  
  
  