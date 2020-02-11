---
title: SQL Server Profiler-limite des compteurs de performances | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.performancecounterlimit.f1
helpviewer_keywords:
- Performance Counters List dialog box
ms.assetid: d10140ef-36c4-449c-b365-1cff1b2524e4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e64c5cc39ed8634ef2ec74f8680c84f7b66b98f1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088823"
---
# <a name="sql-server-profiler---performance-counters-limit"></a>Générateur de profils SQL Server - Limite des compteurs de performances
  Utilisez la boîte de dialogue Limite des compteurs de performances pour limiter les informations provenant d'un fichier journal de performances du Moniteur système lors de sa corrélation avec une trace du [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] . Cette boîte de dialogue vous permet de sélectionner les compteurs qui doivent être affichés et utilisés pour la corrélation.  
  
 La boîte de dialogue **Limite des compteurs de performances** est remplie avec les objets et compteurs de performances contenus dans le fichier journal de performances.  
  
### <a name="to-select-performance-objects-and-counters-to-correlate-with-a-trace"></a>Pour sélectionner les objets et compteurs de performances à corréler avec une trace  
  
1.  Développez un objet de performance pour déterminer les compteurs qui sont inclus dans le fichier journal de performances.  
  
2.  Activez les compteurs que vous souhaitez corréler avec le fichier de trace du [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] .  
  
     Si vous souhaitez sélectionner tous les compteurs pour un objet de performance, activez la case à cocher adjacente à celui-ci. L'activation du nœud de premier niveau, qui indique l'ordinateur, entraîne la sélection de tous les objets et compteurs de performances contenus dans le fichier journal de performances.  
  
## <a name="see-also"></a>Voir aussi  
 [Mettre en corrélation une trace avec les données du journal de performances Windows &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)  
  
  
