---
title: Suspendre une trace (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- pausing traces
- temporarily stopping traces
- traces [SQL Server], pausing
- stopping traces
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
author: stevestein
ms.author: sstein
ms.openlocfilehash: cdc9dbbd01099b1d33787a72b0bd59b65cea722e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054334"
---
# <a name="pause-a-trace-sql-server-profiler"></a>Suspendre une trace (SQL Server Profiler)
  Le fait de marquer une pause dans une trace empêche la capture de nouvelles données d’événement jusqu'au redémarrage de la trace.  
  
 Lorsque vous suspendez une trace, vous empêchez  la capture des données d’événements jusqu'à ce que vous redémarriez la trace. Le redémarrage d'une trace permet de reprendre les opérations de trace. Aucune donnée de trace précédente n'est perdue après le redémarrage. Lors du redémarrage de la trace, la capture des données reprend à partir du point où elle s'était arrêtée. Lorsqu'une trace est suspendue, vous pouvez modifier le nom, les événements, les colonnes et les filtres. Toutefois, vous ne pouvez pas modifier les destinations des données de la trace, ni la connexion au serveur.  
  
### <a name="to-pause-a-trace"></a>Pour interrompre une trace  
  
1.  Sélectionnez une fenêtre contenant une trace en cours d'exécution.  
  
2.  Dans le menu **Fichier** , cliquez sur **Suspendre la trace**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
