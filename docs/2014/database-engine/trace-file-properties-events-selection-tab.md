---
title: Propriétés du fichier de trace (onglet sélection des événements) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracefileproperties.eventsselection.f1
helpviewer_keywords:
- Trace File Properties dialog box
ms.assetid: 158d442f-2225-4173-8545-fb1cf611b4d0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 20ec4981a7a4c7f2d09315416deddc5e0e195fda
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928356"
---
# <a name="trace-file-properties-events-selection-tab"></a>Propriétés du fichier de suivi (onglet Sélection des événements)
  Utilisez l'onglet **Sélection des événements** de la boîte de dialogue **Propriétés du modèle de trace** pour consulter les propriétés des colonnes de la trace ou pour supprimer des colonnes de données de la trace.  
  
 Pour afficher cette fenêtre, ouvrez un fichier de trace. Ensuite, dans le menu **Fichier** , cliquez sur **Propriétés**, puis cliquez sur l'onglet **Sélection des événements** .  
  
## <a name="options"></a>Options  
 Colonne**Events**  
 Affiche les événements tracés organisés par catégorie. Initialement, tous les événements de la trace sont sélectionnés. Sélectionnez les événements requis en activant ou en désactivant les cases à cocher correspondant à une colonne de données d'un événement. Si une case d'événement est cochée, toutes les colonnes de données de cet événement sont sélectionnées. Si la colonne de données d'un événement est cochée, l'événement l'est aussi, de même que toutes les autres colonnes requises. Lors de l'affichage d'une table ou d'un fichier de trace, la désactivation des cases à cocher de certains événements ou de colonnes de données réduit la quantité de données visibles dans la fenêtre de trace, ce qui facilite les analyses. Pour réduire la quantité d'informations visibles, vous pouvez également modifier les filtres de colonne. Pour plus d'informations sur les classes d'événements, consultez [Référence de classe d'événements SQL Server](../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
 Colonnes de données  
 Colonnes de données tracées. Toutes les colonnes de données pertinentes de la trace sont cochées par défaut pour chaque événement inclus dans la trace.  
  
 Spécifiez les filtres en cliquant sur les en-têtes de colonne de données et entrant les critères du filtre. Les colonnes de données filtrées sont indiquées par une icône de filtre à gauche de l'étiquette de colonne dans la boîte de dialogue **Modifier le filtre** .  
  
 **Afficher tous les événements**  
 Affiche tous les événements disponibles. Par défaut, seules les lignes sélectionnées dans la grille **Sélection des événements** sont affichées. Désactivez cette case à cocher pour masquer tous les événements non sélectionnés dans la grille **Sélection des événements** . Si la case **Afficher tous les événements** est cochée et que vous visualisez un fichier ou une table de trace, tous les événements enregistrés dans la trace s'affichent dans la fenêtre de trace.  
  
 **Afficher toutes les colonnes**  
 Affiche toutes les colonnes de données disponibles. Par défaut, seules les colonnes de données sélectionnées sont affichées. Désactivez cette case à cocher pour masquer toutes les colonnes de données non sélectionnées dans la grille **Sélection des événements** .  
  
 **Filtres de colonnes**  
 Ouvre la boîte de dialogue **Modifier le filtre** , dans laquelle une icône de filtre apparaît à gauche de l’étiquette des colonnes de données filtrées. La boîte de dialogue **Modifier le filtre** vous permet de modifier les filtres des colonnes de données.  
  
 **Organiser les colonnes**  
 Après avoir sélectionné les colonnes **Événements** et de données à inclure dans la trace, cliquez sur **Organiser les colonnes** pour forcer la réorganisation dans la grille des colonnes de la fenêtre des résultats de la trace.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifiez les événements et les colonnes de données d’un fichier de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Filtrer les événements dans une trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)   
 [Afficher les informations de filtre &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)   
 [Modifier un filtre &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)   
 [Modèles et autorisations du générateur de SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
  
  
