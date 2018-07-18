---
title: Relire jusqu'à un point d’arrêt (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- breakpoints [SQL Server]
- traces [SQL Server], replaying
ms.assetid: 3caf751e-df3b-40c7-b5e8-4490ae178e0c
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef7c27eff6efd66d95a61a158a0f788f35757182
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289865"
---
# <a name="replay-to-a-breakpoint-sql-server-profiler"></a>Relecture jusqu'à un point d'arrêt (SQL Server Profiler)
  Cette rubrique explique comment définir des points d'arrêt dans un fichier ou une table de trace que vous souhaitez relire à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. La définition de points d'arrêt dans un fichier ou une table de trace avant de démarrer la relecture de cette dernière vous permet de suspendre la relecture de la trace lorsque surviennent des événements spécifiques. L'utilisation de points d'arrêt pendant la relecture d'une trace n'empêche pas le débogage. Vous pouvez en effet fractionner la relecture de scripts de trace longs en petits segments, qui peuvent être analysés de façon incrémentielle.  
  
### <a name="to-replay-to-a-breakpoint"></a>Pour relire jusqu'à un point d'arrêt  
  
1.  Ouvrez le fichier de trace ou la table de trace à relire. Pour plus d’informations, consultez [Ouvrir un fichier de trace&#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) ou [Ouvrir une table de trace &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).  
  
     Vérifiez que le fichier de trace ou la table de trace que vous ouvrez contient les classes d'événements nécessaires pour la relecture. Pour plus d’informations, consultez [Conditions préalables à la relecture](replay-requirements.md).  
  
2.  Dans la fenêtre de trace, cliquez sur un événement à utiliser comme point d'arrêt. Pour définir un point d'arrêt, employez l'une des trois méthodes suivantes :  
  
    -   Appuyez sur F9.  
  
    -   Dans le menu **Relire** , cliquez sur **Basculer le point d’arrêt**.  
  
    -   Cliquez avec le bouton droit sur l’événement, puis cliquez sur **Basculer le point d’arrêt**.  
  
     Une puce rouge apparaît en regard de l'événement de trace sélectionné, indiquant qu'il s'agit du point d'arrêt.  
  
     Répétez cette étape pour définir plusieurs points d'arrêt.  
  
3.  Dans le menu **Relire** , cliquez sur **Démarrer**, puis connectez-vous au serveur sur lequel vous souhaitez relire la trace.  
  
4.  Dans la boîte de dialogue **Configuration de la relecture** , vérifiez les paramètres, puis cliquez sur **OK**.  
  
     La relecture démarre pour s'interrompre une fois le point d'arrêt atteint.  
  
5.  Appuyez sur F5 pour reprendre la relecture jusqu'au point d'arrêt suivant.  
  
6.  Répétez l'étape 5 jusqu'à la fin de la trace.  
  
## <a name="see-also"></a>Voir aussi  
 [Relire jusqu'à un curseur &#40;SQL Server Profiler&#41;](replay-to-a-cursor-sql-server-profiler.md)   
 [Relire des Traces](replay-traces.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
