---
title: Boîte de dialogue SQL Server Profiler-Rechercher | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 81ed454290a5ca62093fe9bdb619179106ca9985
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66088854"
---
# <a name="sql-server-profiler---find-dialog-box"></a>Générateur de profils SQL Server (boîte de dialogue Rechercher)
  Utilisez la boîte de dialogue **Rechercher** pour rechercher une trace de caractères ou de mots spécifiques. Pour annuler une recherche en cours, appuyez sur ÉCHAP.  
  
 Dans le menu [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]Edition **, cliquez sur** Rechercher **pour ouvrir cette boîte de dialogue dans**.  
  
## <a name="options"></a>Options  
 **Rechercher**  
 Entrez le texte à rechercher. La recherche retourne toute chaîne contenant la chaîne spécifiée. Par exemple, si vous recherchez "Completed", la chaîne "SQL:BatchCompleted" est retournée. Les caractères génériques (*, ?, etc.) ne sont pas pris en charge.  
  
 **Rechercher dans la colonne**  
 Cliquez sur une colonne de données à rechercher, ou cliquez sur ** \<toutes les colonnes>** pour effectuer une recherche dans toutes les colonnes de données de la trace.  
  
 **Respecter la casse**  
 Recherche du texte présentant la même casse que celui spécifié dans la zone **Rechercher** . Désactivez cette case à cocher pour rechercher dans la trace des correspondances avec les caractères indiqués mais sans distinction entre les majuscules et les minuscules.  
  
 **Mot entier**  
 Restreint la recherche à des mots entiers. Décochez la case **Mot entier** pour rechercher des caractères spécifiques au sein d’un mot.  
  
 **Suivant**  
 Recherche la correspondance suivante avec les caractères spécifiés dans la zone **Rechercher** .  
  
 **Précédent**  
 Recherche dans la trace la correspondance précédente avec les caractères spécifiés dans la zone **Rechercher** .  
  
## <a name="see-also"></a>Voir aussi  
 [Rechercher une valeur ou une colonne de données pendant le suivi &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)   
 [Créer un &#40;de trace SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [Ouvrez une table de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [Ouvrir un fichier de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [SQL Server Profiler les modèles et les autorisations](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
