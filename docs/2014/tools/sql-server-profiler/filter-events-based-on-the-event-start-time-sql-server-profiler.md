---
title: Filtrer des événements en fonction de leur heure de début (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0cd08ce16341022072c76fc1bf073d1a469d9273
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63192903"
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a>Filtrer des événements en fonction de l'heure de début de l'événement (SQL Server Profiler)
  Cette rubrique explique comment filtrer des événements de trace en fonction de leur heure de début à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a>Pour filtrer un événement en fonction de son heure de début  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     La boîte de dialogue **Propriétés de la trace**apparaît.  
  
    > [!NOTE]  
    >  Si la case **Démarrer le suivi juste après avoir établi la connexion**est cochée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et le suivi se lance. Pour désactiver ce paramètre, accédez au menu **Outils**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la zone **Nom de la trace** , tapez un nom pour la trace.  
  
3.  Dans la liste de noms **Utiliser le modèle**, sélectionnez un modèle de trace.  
  
4.  Le cas échéant, spécifiez une destination pour les résultats de la trace.  
  
5.  Sous l’onglet **Sélection des événements**, cliquez sur l’en-tête de colonne **StartTime** . Vous pouvez également cliquer avec le bouton droit sur l’en-tête puis cliquer sur **Modifier le filtre des colonnes** pour ouvrir la boîte de dialogue **Modifier le filtre** .  
  
6.  Développez **supérieur** ou **inférieure à**, puis entrez un `datetime` valeur dans le champ qui apparaît sous l’opérateur de comparaison.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
