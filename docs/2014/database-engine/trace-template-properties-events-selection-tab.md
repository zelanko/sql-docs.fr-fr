---
title: Propriétés du modèle de trace (onglet sélection des événements) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetemplateproperties.eventsselection.f1
helpviewer_keywords:
- Trace Template Properties dialog box
ms.assetid: 5b202457-ab42-4902-8012-7f3f40aa09f5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f70460e68d1161fa8aa718a5e5264a8e6f0782df
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928164"
---
# <a name="trace-template-properties-events-selection-tab"></a>Propriétés du modèle de trace (onglet Sélection des événements)
  L'onglet **Sélection des événements** de la boîte de dialogue **Propriétés du modèle de trace** vous permet d'afficher, de modifier ou de spécifier les classes d'événements et les colonnes de données à inclure dans un modèle de trace [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] .  
  
## <a name="options"></a>Options  
 Colonne**Events**  
 Permet de spécifier les événements à tracer en activant ou en désactivant la case à cocher dans la colonne d'événement. Les événements sont organisés par catégorie d'événement.  
  
 Si vous avez sélectionné **Baser le nouveau modèle sur un modèle existant** sous l'onglet **Général** , des événements sont sélectionnés automatiquement en fonction du modèle spécifié. Pour plus d'informations sur les classes d'événements, consultez [Référence de classe d'événements SQL Server](../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
 Colonnes de données  
 Permet de spécifier les colonnes de données à tracer en activant la case à cocher qui correspond à la colonne d'événement et de données dont vous avez besoin. Toutes les colonnes d'événements appropriées sont sélectionnées par défaut pour chaque événement inclus dans la trace, si la case à cocher correspondant à l'événement est activée. Si vous avez activé **Baser le nouveau modèle sur un modèle existant** sous l'onglet **Général** , les colonnes de données et les filtres sont sélectionnés automatiquement en fonction du modèle spécifié.  
  
 Spécifiez les filtres en cliquant sur les en-têtes de colonne de données et entrant les critères du filtre. Les colonnes de données filtrées sont indiquées par une icône de filtre à gauche de l'étiquette de colonne dans la boîte de dialogue **Modifier le filtre** .  
  
 **Afficher tous les événements**  
 Affiche tous les événements disponibles. Cette option est activée par défaut si vous créez un nouveau modèle qui n'est pas basé sur un modèle existant. Désactivez l'option pour masquer tous les événements non sélectionnés dans la grille **Sélection des événements** .  
  
 **Afficher toutes les colonnes**  
 Affiche toutes les colonnes de données disponibles. Cette option est activée par défaut si vous créez un nouveau modèle qui n'est pas basé sur un modèle existant. Désactivez l'option pour masquer toutes les colonnes de données non sélectionnées dans la grille **Sélection des événements** .  
  
 **Filtres de colonnes**  
 Lance la boîte de dialogue **Modifier le filtre**, qui affiche une icône de filtre à gauche de l’étiquette d’une colonne de données. La boîte de dialogue **Modifier le filtre** vous permet de modifier les filtres des colonnes de données.  
  
 **Organiser les colonnes**  
 Modifie l'ordre des colonnes dans la trace et regroupe les résultats suivant une ou plusieurs colonnes.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifiez les événements et les colonnes de données d’un fichier de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Organiser les colonnes affichées dans une trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)   
 [Filtrer les événements dans une trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)   
 [Afficher les informations de filtre &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)   
 [Modifier un filtre &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)   
 [Modèles et autorisations du générateur de SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
