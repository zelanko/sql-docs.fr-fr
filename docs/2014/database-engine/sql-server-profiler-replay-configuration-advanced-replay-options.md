---
title: SQL Server Profiler-configuration de la relecture (options de relecture avancées) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.advanced.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: b4eb34f7-3af6-4a44-ba7e-2b8430ec3cd7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 78ca3fc2d11b22d70c8a4e99d0961f793870bd53
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84928515"
---
# <a name="sql-server-profiler---replay-configuration-advanced-replay-options"></a>Générateur de profils SQL Server - Configuration de la relecture (Options de relecture avancées)
  Dans la boîte de dialogue **Configuration de la relecture** , utilisez l’onglet **Options de relecture avancées** pour spécifier le mode de relecture d’un fichier de trace.  
  
 Pour afficher cette fenêtre, utilisez le [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] pour ouvrir un fichier de trace ou une table qui contient les événements appropriés pour la relecture. Pour plus d’informations, consultez [Conditions préalables à la relecture](../tools/sql-server-profiler/replay-requirements.md). Après avoir ouvert le fichier de trace ou la table, dans le menu **Relecture** , cliquez sur **Démarrer**, connectez-vous à l’instance de SQL Server sur laquelle vous voulez relire la trace, puis cliquez sur l’onglet **Options de relecture avancées** .  
  
## <a name="options"></a>Options  
 **Relire les SPID système**  
 Spécifie si le [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] relit les SPID système.  
  
 **Relire un SPID uniquement**  
 Ne relit que l'activité du fichier de trace source qui est relative au SPID sélectionné.  
  
 **SPID à relire**  
 Spécifiez le SPID à relire.  
  
 **Limiter la relecture par date et heure**  
 Activez cette option pour ne relire qu'une partie du fichier de trace source.  
  
 **Heure de début**  
 Date et heure auxquelles la relecture doit commencer dans le fichier de trace source.  
  
 **Heure de fin**  
 Date et heure auxquelles la relecture doit se terminer dans le fichier de trace source.  
  
 **Délai d'attente du moniteur d'intégrité (sec.)**  
 Spécifiez le délai d'attente de la relecture, en secondes. La valeur par défaut est 3 600 secondes (1 heure). Ce paramètre affecte la durée d'exécution d'un processus autorisée avant son interruption par le moniteur d'intégrité.  
  
 **Intervalle d'interrogation du moniteur d'intégrité par défaut (sec)**  
 Spécifiez, en secondes, l'intervalle d'interrogation du moniteur d'intégrité pendant la relecture. La valeur par défaut est 60 secondes. Cette valeur permet à l'utilisateur de configurer la fréquence à laquelle le moniteur d'intégrité interroge les candidats à l'arrêt.  
  
 **Activer le moniteur de processus bloqués de SQL Server**  
 Active un processus qui recherche les processus bloqués ou les processus de blocage.  
  
 **Délai d'attente du moniteur de processus bloqués (s)**  
 Configure la fréquence à laquelle le moniteur de processus recherche les processus bloqués ou les processus de blocage.  
  
## <a name="see-also"></a>Voir aussi  
 [Relire une table de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [Relire un fichier de trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [Relire des traces](../tools/sql-server-profiler/replay-traces.md)  
  
  
