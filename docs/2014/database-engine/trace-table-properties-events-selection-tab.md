---
title: Propriétés (onglet Sélection des événements) de la Table de trace | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetableproperties.eventsselection.f1
helpviewer_keywords:
- Trace Table Properties dialog box
ms.assetid: fa21df6a-b6b5-4b15-9104-957385821594
caps.latest.revision: 23
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 28084e041538412399e518856ef4d948add75def
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250559"
---
# <a name="trace-table-properties-events-selection-tab"></a>Propriétés de la table de trace (onglet Sélection des événements)
  Utilisez l'onglet **Sélection des événements** de la boîte de dialogue **Propriétés de la table de trace** pour afficher les propriétés des colonnes de données et d'événements dans la trace ou pour supprimer de tels événements ou colonnes.  
  
 Pour afficher cette fenêtre, utilisez le [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] pour ouvrir un fichier de trace. Dans le menu **Fichier** , cliquez sur **Propriétés**puis sur l'onglet **Sélection des événements** .  
  
## <a name="options"></a>Options  
 Colonne **Événements**  
 Affiche les événements tracés organisés par catégorie. Sélectionnez les événements requis en activant ou en désactivant les cases à cocher correspondant à une colonne de données d'un événement. Si une case d'événement est cochée, toutes les colonnes de données de cet événement sont sélectionnées. Si la colonne de données d'un événement est cochée, l'événement l'est aussi, de même que toutes les autres colonnes requises. Lors de l'affichage d'une table ou d'un fichier de trace, la désactivation des cases à cocher de certains événements ou de colonnes de données réduit la quantité de données visibles dans la fenêtre de trace, ce qui facilite les analyses. Pour réduire la quantité d'informations visibles, vous pouvez également modifier les filtres de colonne. Pour plus d'informations sur les classes d'événements, consultez [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
 Autres colonnes de données  
 Colonnes de données tracées. Toutes les colonnes de données pertinentes de la trace sont cochées par défaut pour chaque événement inclus dans la trace.  
  
 Spécifiez les filtres en cliquant sur les en-têtes de colonne de données et entrant les critères du filtre. Les colonnes de données filtrées sont indiquées par une icône de filtre à gauche de l'étiquette de colonne dans la boîte de dialogue **Modifier le filtre** .  
  
 **Afficher tous les événements**  
 Affiche tous les événements disponibles. Par défaut, seules les lignes sélectionnées dans la grille **Sélection des événements** sont affichées. Désactivez cette case à cocher pour masquer tous les événements non sélectionnés dans la grille **Sélection des événements** . Si **elle** est activée, lors de l'affichage d'une table ou d'un fichier de trace, tous les événements enregistrés dans la trace s'affichent dans la fenêtre de trace.  
  
 **Afficher toutes les colonnes**  
 Affiche toutes les colonnes de données disponibles. Par défaut, seules les colonnes de données sélectionnées sont affichées. Désactivez cette case à cocher pour masquer toutes les colonnes de données non sélectionnées dans la grille **Sélection des événements** .  
  
 **Filtres de colonnes**  
 Affiche la boîte de dialogue **Modifier le filtre**, avec une icône de filtre à gauche de l’étiquette de colonne. Vous pouvez utiliser celle-ci pour modifier les filtres de colonnes de données.  
  
 **Organiser les colonnes**  
 Après avoir sélectionné les colonnes **Événements** et de données à inclure dans la trace, cliquez sur **Organiser les colonnes** pour forcer la réorganisation dans la grille des colonnes de la fenêtre des résultats de la trace.  
  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir une table de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [Modèles et autorisations du générateur de SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
