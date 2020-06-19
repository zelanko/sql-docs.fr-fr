---
title: SQL Server Profiler-configuration de la relecture (options de relecture de base) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: 85a1dec6-9bbc-477a-86c5-b463db9ebb31
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5d95ca6c63903adff866ce0e6c25146b8e77d6b1
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928570"
---
# <a name="sql-server-profiler---replay-configuration-basic-replay-options"></a>Générateur de profils SQL Server – Configuration de la relecture (Options de relecture de base)
  Dans la boîte de dialogue **Configuration de la relecture**, utilisez la page **Options de relecture de base** pour spécifier la manière de relire un fichier ou une table de trace.  
  
 Pour afficher cette fenêtre, utilisez le [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] pour ouvrir un fichier de trace ou une table qui contient les événements appropriés pour la relecture. Pour plus d’informations, consultez [Conditions préalables à la relecture](../tools/sql-server-profiler/replay-requirements.md). Lorsque le fichier ou la table de trace est ouvert, dans le menu **Relire** , cliquez sur **Début**, puis connectez-vous à l’instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dans laquelle vous voulez relire la trace.  
  
## <a name="options"></a>Options  
 **Serveur de relecture**  
 Affiche l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à laquelle se connecter pour la relecture.  
  
 **Modifier...**  
 Affiche la boîte de dialogue **Se connecter au serveur** pour se connecter à un autre serveur.  
  
 **Enregistrer dans le fichier**  
 Permet d'enregistrer les résultats de relecture dans un fichier. [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] affiche la boîte de dialogue de fichier standard, qui vous permet de spécifier l’emplacement où enregistrer le fichier.  
  
 **Enregistrer dans la table**  
 Permet d'enregistrer les résultats de relecture dans une table. [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] affiche la boîte de dialogue de sélection de table, qui vous permet de spécifier l’emplacement où enregistrer la table.  
  
 **Nombre de threads de relecture**  
 Spécifiez le nombre de threads de relecture à utiliser simultanément. Plus ce nombre est important, plus la relecture consomme de ressources, mais plus elle est rapide.  
  
 **Relire les événements selon leur ordre de suivi**  
 Permet de relire les événements de manière séquentielle. Utilisez cette option pour relire une trace pour un débogage.  
  
 **Relire les événements en utilisant plusieurs threads**  
 Permet de relire les événements de manière simultanée. Cette option est plus rapide que la relecture séquentielle des événements, mais elle désactive le débogage. Les événements sont ordonnés à l'aide de leurs identificateurs de processus système (SPID).  
  
 **Afficher les résultats de relecture**  
 Permet d'afficher les résultats de relecture dans [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Relire une table de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [Relire un fichier de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [Relire des traces](../tools/sql-server-profiler/replay-traces.md)  
  
  
