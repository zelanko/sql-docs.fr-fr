---
title: Filtrer des événements en fonction de leur heure de fin
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 8372ce58317eead122675f3585be01f5da7eb829
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307266"
---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a>Filtrer des événements en fonction de leur heure de fin (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique explique comment filtrer des événements de trace en fonction de leur heure de fin à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a>Pour filtrer des événements en fonction de leur heure de fin  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     La boîte de dialogue **Propriétés de la trace**apparaît.  
  
    > [!NOTE]  
    >  Si la case **Démarrer le suivi juste après avoir établi la connexion**est cochée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et le suivi se lance. Pour désactiver ce paramètre, accédez au menu **Outils**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la boîte de dialogue **Propriétés de la trace** , assurez-vous que l'onglet **Général** est sélectionné, puis entrez un nom dans la zone de texte **Nom de la trace** .  
  
3.  Dans la liste **Utiliser le modèle**, sélectionnez un modèle de trace.  
  
4.  Le cas échéant, spécifiez un fichier ou une table de destination pour y enregistrer les résultats du suivi.  
  
5.  Dans le menu **Sélection des événements**, cliquez sur la colonne de données **Heure de fin** pour ouvrir la boîte de dialogue **Modifier le filtre** . Vous pouvez également cliquer avec le bouton droit sur l’en-tête de la colonne, puis sélectionner **Modifier le filtre des colonnes**.  
  
6.  Développez **Supérieur à** ou **Inférieur à**, puis entrez une valeur **datetime**dans le champ qui apparaît sous l’opérateur de comparaison.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
