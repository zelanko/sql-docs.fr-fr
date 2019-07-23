---
title: Afficher les informations de filtre (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 94cdf7dcde876b18a6080eefb5afde8137d2e021
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059613"
---
# <a name="view-filter-information-sql-server-profiler"></a>Afficher des informations de filtre (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique indique comment afficher des filtres sur des colonnes de données pour des classes d'événements en utilisant [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-view-filter-information"></a>Pour afficher les informations de filtrage  
  
1.  Ouvrez un fichier de trace, une table de trace ou un script SQL, et dans le menu **Fichier** , cliquez sur **Propriétés**. Si vous modifiez un modèle de trace ou créez une nouvelle trace, ignorez cette étape.  
  
2.  Sous l’onglet **Sélection des événements** , cliquez avec le bouton droit sur le nom de la colonne de données du filtre à afficher, puis cliquez sur **Modifier le filtre des colonnes**.  
  
3.  Dans la boîte de dialogue **Modifier le filtre** , développez les opérateurs de comparaison de filtre pour afficher la valeur affectée pour le critère spécifié. Recommencez les étapes 2 et 3 pour toutes les colonnes pour lesquelles vous souhaitez afficher des informations de filtre.  
  
> [!NOTE]  
>  Les opérateurs de comparaison avec des valeurs affectées apparaissent en caractères gras.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
