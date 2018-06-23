---
title: SQL Server Profiler - Source Table-Paramétrage moteur base données - sélectionner la Table de charge de travail | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.pro.replay.tools.sourcetable.f1
helpviewer_keywords:
- Select Workload Table dialog box
- Source Table dialog box
ms.assetid: 51185be7-7092-480a-a52c-cf7786c4a0a0
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8b5ccfddb032fb3833e517632290cfdf7d82e643
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040457"
---
# <a name="sql-server-profiler---source-table-database-engine-tuning-advisor---select-workload-table"></a>Table SQL Server Profiler - moteur de base de données de la Table Source Assistant Paramétrage du - sélectionnez charge de travail
  Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] et l'Assistant Paramétrage de [!INCLUDE[ssDE](../includes/ssde-md.md)] utilisent cette boîte de dialogue pour sélectionner des tables.  
  
 Dans [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], utilisez la boîte de dialogue **Table source** pour spécifier une table source pour une table de trace. Ceci est une table à partir de laquelle une trace est chargée et dont le contenu est affiché ou utilisé pour relire la trace.  
  
 Dans l’Assistant Paramétrage de [!INCLUDE[ssDE](../includes/ssde-md.md)], utilisez la boîte de dialogue **Sélectionner une table de charge de travail** pour sélectionner une table de base de données qui contient les informations de trace [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] à utiliser comme charge de travail de paramétrage, ou pour afficher l’aperçu du contenu de la table avant de commencer l’analyse du paramétrage.  
  
## <a name="options"></a>Options  
 **SQL Server**  
 Spécifie l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] actuellement connectée. Ce champ est rempli automatiquement et ne peut pas être mis à jour.  
  
 **Sauvegarde de la base de données**  
 Spécifie la base de données dans laquelle se trouve la table de trace.  
  
 **Propriétaire**  
 Specifies the owner of the trace table. Ce champ est rempli automatiquement comme **dbo**.  
  
 **Table**  
 Spécifie le nom de la table de trace à partir de laquelle la trace doit être lue.  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les résultats de Trace dans une Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)   
 [Modèles et autorisations du générateur de SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Assistant Paramétrage du moteur de base de données](../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  