---
title: Afficher les informations de filtre (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 931b83f8087d446cfc7b08d9582cbad5b02cf671
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85007006"
---
# <a name="view-filter-information-sql-server-profiler"></a>Afficher des informations de filtre (SQL Server Profiler)
  Cette rubrique indique comment afficher des filtres sur des colonnes de données pour des classes d'événements en utilisant [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-view-filter-information"></a>Pour afficher les informations de filtrage  
  
1.  Ouvrez un fichier de trace, une table de trace ou un script SQL, et dans le menu **Fichier** , cliquez sur **Propriétés**. Si vous modifiez un modèle de trace ou créez une nouvelle trace, ignorez cette étape.  
  
2.  Sous l’onglet **Sélection des événements** , cliquez avec le bouton droit sur le nom de la colonne de données du filtre à afficher, puis cliquez sur **Modifier le filtre des colonnes**.  
  
3.  Dans la boîte de dialogue **Modifier le filtre** , développez les opérateurs de comparaison de filtre pour afficher la valeur affectée pour le critère spécifié. Recommencez les étapes 2 et 3 pour toutes les colonnes pour lesquelles vous souhaitez afficher des informations de filtre.  
  
> [!NOTE]  
>  Les opérateurs de comparaison avec des valeurs affectées apparaissent en caractères gras.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
