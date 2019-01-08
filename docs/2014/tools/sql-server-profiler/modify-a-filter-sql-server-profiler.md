---
title: Modifier un filtre (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], modifying
- modifying filters, modifying
- filters [SQL Server], traces
ms.assetid: 8b317813-4918-4485-b930-77b1951aa00c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: db6d6220fbb0f756b539e63dc2496d9ddb46d9f5
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52775401"
---
# <a name="modify-a-filter-sql-server-profiler"></a>Modifier un filtre (SQL Server Profiler)
  Vous ajoutez des filtres pour tracer des modèles, qui contiennent les définitions de trace, afin de limiter le nombre d'événements recueillis par une trace. La limitation du nombre d'événements recueillis peut atténuer les effets du traçage sur les performances. Si vous définissez des filtres pour un modèle de trace et remarquez que la trace ne recueille pas le type d'informations dont vous avez besoin, vous pouvez modifier le filtre.  
  
### <a name="to-modify-a-filter"></a>Pour modifier un filtre  
  
1.  Dans [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], ouvrez le modèle du filtre de trace à modifier. Dans le menu **Fichier** , cliquez sur **Modèles**, puis choisissez **Modifier le modèle**.  
  
2.  Dans la boîte de dialogue **Propriétés du modèle de trace** , sous l’onglet **Général** , sélectionnez un modèle dans la liste **Sélectionner le nom du modèle** .  
  
3.  Cliquez sur l’onglet **Sélection des événements** .  
  
     L’onglet **Sélection des événements** contient un contrôle de grille. Le contrôle de grille est une table qui contient chacune des classes d'événements traçables. La table contient une ligne par classe d'événements. Les classes d'événements peuvent différer légèrement, selon le type et la version du serveur auquel vous êtes connecté. Les classes d’événements sont identifiées dans la colonne **Events**de la grille, et groupées par catégorie d’événement. Les autres colonnes répertorient les colonnes de données pouvant être retournées pour chaque classe d'événements.  
  
4.  Cliquez sur **Filtres de colonnes**.  
  
5.  Dans la boîte de dialogue **Modifier le filtre** , cliquez sur la valeur en regard de l’opérateur de comparaison à modifier, puis tapez la nouvelle valeur ou supprimez une valeur. Vous pouvez également ajouter des filtres supplémentaires.  
  
6.  Cliquez sur **OK** et enregistrez le modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
