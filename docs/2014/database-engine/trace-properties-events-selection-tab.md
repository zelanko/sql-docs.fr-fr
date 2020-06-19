---
title: Propriétés de la trace (onglet sélection des événements) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.eventsselection.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: e1892f24-7272-4d5d-8926-6150cc82b2c3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b3644ecee04dd177c792efcb02ad75f91baa46c9
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928294"
---
# <a name="trace-properties-events-selection-tab"></a>Propriétés de la trace (onglet Sélection des événements)
  Utilisez l'onglet **Sélection des événements** de la boîte de dialogue **Propriétés de la trace** pour afficher ou spécifier les événements à tracer et les colonnes de données.  
  
## <a name="options"></a>Options  
 Colonne**Events**  
 Spécifiez les événements à tracer en activant ou en désactivant les cases à cocher dans la colonne des événements. Les**événements** sont organisés par catégorie. Les classes d'événements spécifiées dans le modèle sont automatiquement sélectionnées. Pour plus d'informations, consultez [Référence de classe d'événements SQL Server](../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
 Colonnes de données  
 Précisez les colonnes de données à tracer en activant la case à cocher correspondant à l'événement et à la colonne de données requis. Toutes les colonnes d'événements pertinentes sont cochées par défaut pour chaque événement inclus dans la trace.  
  
 Spécifiez les filtres en cliquant sur les en-têtes de colonne de données et entrant les critères du filtre. Les colonnes de données filtrées sont indiquées par une icône de filtre à gauche de l'étiquette de colonne dans la boîte de dialogue **Modifier le filtre** . Pour plus d’informations, consultez [SQL Server Profiler - Modifier le filtre](../../2014/database-engine/sql-server-profiler-edit-filter.md).  
  
 **Afficher tous les événements**  
 Affiche tous les événements disponibles. Par défaut, seules les lignes sélectionnées dans la grille **Sélection des événements** sont affichées. Désactivez cette case à cocher pour masquer tous les événements non sélectionnés dans la grille **Sélection des événements** .  
  
 **Afficher toutes les colonnes**  
 Affiche toutes les colonnes de données disponibles. Par défaut, seules les colonnes de données sélectionnées sont affichées. Désactivez cette case à cocher pour masquer toutes les colonnes de données non sélectionnées dans la grille **Sélection des événements** .  
  
 **Filtres de colonnes**  
 Affiche la boîte de dialogue **Modifier le filtre** . Vous pouvez utiliser celle-ci pour modifier les filtres de colonnes de données.  
  
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
  
  
