---
title: "Filtrer des événements en fonction de l’heure de fin (SQL Server Profiler) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event end times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 650c9e7cd67a4e6ebdc6278bc4f6db491bb0e478
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a>Filtrer des événements en fonction de leur heure de fin (SQL Server Profiler)
  Cette rubrique explique comment filtrer des événements de trace en fonction de leur heure de fin à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a>Pour filtrer des événements en fonction de leur heure de fin  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     La boîte de dialogue **Propriétés de la trace**apparaît.  
  
    > [!NOTE]  
    >  Si la case **Démarrer le suivi juste après avoir établi la connexion**est cochée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et le suivi se lance. Pour désactiver ce paramètre, dans le menu **Outils**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la boîte de dialogue **Propriétés de la trace** , assurez-vous que l'onglet **Général** est sélectionné, puis entrez un nom dans la zone de texte **Nom de la trace** .  
  
3.  Dans la liste **Utiliser le modèle**, sélectionnez un modèle de trace.  
  
4.  Le cas échéant, spécifiez un fichier ou une table de destination pour y enregistrer les résultats du suivi.  
  
5.  Dans le menu **Sélection des événements**, cliquez sur la colonne de données **Heure de fin** pour ouvrir la boîte de dialogue **Modifier le filtre** . Vous pouvez également cliquer avec le bouton droit sur l’en-tête de la colonne, puis sélectionner **Modifier le filtre des colonnes**.  
  
6.  Développez **Supérieur à** ou **Inférieur à**, puis entrez une valeur **datetime**dans le champ qui apparaît sous l’opérateur de comparaison.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

