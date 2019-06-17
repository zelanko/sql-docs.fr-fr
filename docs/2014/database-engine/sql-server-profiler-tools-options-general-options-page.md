---
title: SQL Server Profiler - Outils-Options (Page d’Options Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.generaloptions.f1
helpviewer_keywords:
- General Options dialog box
ms.assetid: a888246d-ccfe-415f-bbdc-d6adafac250a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c9da36f49927acd2a313bcb9f8647655731006d2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66089619"
---
# <a name="sql-server-profiler---tools-options-general-options-page"></a>SQL Server Profiler - Outils-Options (Page d’Options Général)
  Utilisez la boîte de dialogue **Options générales** pour afficher ou spécifier les options ci-après.  
  
## <a name="options"></a>Options  
  
### <a name="display-options"></a>Options d'affichage  
 **Nom de police**  
 Affiche le nom de la police utilisée dans la grille des résultats de trace pendant les traces.  
  
 **Taille de la police**  
 Affiche la taille de la police utilisée dans la grille des résultats de trace pendant les traces.  
  
 **Choisir la police**  
 Ouvre une boîte de dialogue permettant de modifier les paramètres de police.  
  
 **Utiliser des paramètres régionaux pour afficher les valeurs de date et d'heure**  
 Affiche les valeurs de date et d'heure selon les paramètres régionaux configurés sur votre ordinateur. Si vous ne sélectionnez pas cette option, les valeurs de date et d'heure sont affichées dans le format fixe de Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], qui comprend les millisecondes.  
  
> [!NOTE]  
>  En cochant et en décochant cette case, vous modifiez le format d’affichage des colonnes de temps comme **StartTime** et **EndTime**. Toutefois, vous ne modifiez pas les paramètres de valeur **DateTime** dans les événements de langage ou les appels de procédure distante (RPC).  
  
 **Afficher les valeurs dans la colonne Durée en microsecondes**  
 Affiche les valeurs en microsecondes dans la colonne de données **Durée** des traces. Par défaut, la colonne **Durée** affiche les valeurs en millisecondes.  
  
### <a name="tracing-options"></a>Options de suivi  
 **Démarrer le suivi juste après avoir établi la connexion**  
 Commence une trace utilisant le modèle par défaut dès qu'une connexion est établie.  
  
 **Mettre à jour la définition de la trace lors de la modification de la version du fournisseur**  
 Applique la définition de trace la plus récente à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] lorsque le fournisseur est mis à jour. Cette option n'est pas activée par défaut. Elle force le [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] à interroger le serveur sur la définition de trace et à recréer le fichier sur le disque le cas échéant.  
  
### <a name="file-rollover-options"></a>Options de substitution de fichier  
 **Charger tous les fichiers de substitution en séquence sans invite**  
 Charge automatiquement les fichiers de substitution lorsqu'un fichier de trace est ouvert. Si plusieurs fichiers ont été créés pendant le suivi, la sélection de cette option charge automatiquement tous les fichiers de substitution.  
  
 **Demander confirmation avant le chargement des fichiers de substitution**  
 Le [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] vous demande confirmation avant l'ajout d'un fichier de substitution lorsqu'un fichier de trace est ouvert.  
  
 **Ne jamais charger les fichiers de substitution suivants**  
 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] ne charge jamais les fichiers de substitution suivants quand un fichier de trace est ouvert.  
  
### <a name="replay-options"></a>Options de relecture  
 **Nombre par défaut de threads de relecture**  
 Spécifiez le nombre de threads de relecture à utiliser simultanément. Un nombre élevé consomme davantage de ressources pendant la relecture, mais améliore la simultanéité de relecture.  
  
 **Délai d'attente du moniteur d'intégrité par défaut (sec)**  
 Spécifiez le délai d'attente de la relecture, en secondes. La valeur par défaut est 3 600 secondes (1 heure). Ce paramètre affecte la durée d'exécution d'un thread autorisée avant son interruption par le moniteur d'intégrité.  
  
 **Intervalle d'interrogation du moniteur d'intégrité par défaut (sec)**  
 Spécifiez, en secondes, l'intervalle d'interrogation du moniteur d'intégrité pendant la relecture. La valeur par défaut est 60 secondes. Cette valeur permet à l'utilisateur de configurer la fréquence à laquelle le moniteur d'intégrité interroge les candidats à l'arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer automatiquement une trace après s’être connecté à un serveur &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [Définir les valeurs par défaut de l’affichage des traces &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)   
 [Relire une table de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [Relire un fichier de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [Relire des traces](../tools/sql-server-profiler/replay-traces.md)   
 [Définir les Options globales des traces &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)   
 [Modèles et autorisations du générateur de SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
