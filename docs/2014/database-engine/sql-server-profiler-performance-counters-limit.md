---
title: SQL Server Profiler - limite des compteurs de performances | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.pro.performancecounterlimit.f1
helpviewer_keywords:
- Performance Counters List dialog box
ms.assetid: d10140ef-36c4-449c-b365-1cff1b2524e4
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2548fbd28af45cbd888a183a739362f0e7767218
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045222"
---
# <a name="sql-server-profiler---performance-counters-limit"></a>Générateur de profils SQL Server - Limite des compteurs de performances
  Utilisez la boîte de dialogue Limite des compteurs de performances pour limiter les informations provenant d'un fichier journal de performances du Moniteur système lors de sa corrélation avec une trace du [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] . Cette boîte de dialogue vous permet de sélectionner les compteurs qui doivent être affichés et utilisés pour la corrélation.  
  
 La boîte de dialogue **Limite des compteurs de performances** est remplie avec les objets et compteurs de performances contenus dans le fichier journal de performances.  
  
### <a name="to-select-performance-objects-and-counters-to-correlate-with-a-trace"></a>Pour sélectionner les objets et compteurs de performances à corréler avec une trace  
  
1.  Développez un objet de performance pour déterminer les compteurs qui sont inclus dans le fichier journal de performances.  
  
2.  Activez les compteurs que vous souhaitez corréler avec le fichier de trace du [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] .  
  
     Si vous souhaitez sélectionner tous les compteurs pour un objet de performance, activez la case à cocher adjacente à celui-ci. L'activation du nœud de premier niveau, qui indique l'ordinateur, entraîne la sélection de tous les objets et compteurs de performances contenus dans le fichier journal de performances.  
  
## <a name="see-also"></a>Voir aussi  
 [Corréler une trace aux données du journal de performances Windows &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)  
  
  