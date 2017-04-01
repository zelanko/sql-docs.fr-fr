---
title: "D&#233;finir les options globales de trace (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "options globales de trace [SQL Server]"
ms.assetid: 2854608a-c3c7-4eb8-b567-034bfec4b1a9
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# D&#233;finir les options globales de trace (SQL Server Profiler)
  Cette rubrique décrit la définition des options qui s'appliquent à toutes les traces créées avec une instance [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] spécifique.  
  
### Pour définir les options globales des traces  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans la boîte de dialogue **Options générales**, cliquez sur **Choisir la police** pour modifier les options d’affichage, puis sur **OK**.  
  
3.  Vous pouvez sélectionner l’option **Démarrer le suivi juste après avoir établi la connexion**.  
  
4.  Vous pouvez également sélectionner l’option **Mettre à jour la définition de la trace lors de la modification de la version du fournisseur**. Cette option fortement recommandée est activée par défaut. Lorsqu'elle est sélectionnée, la définition de la trace est automatiquement mise à jour avec la version actuelle du serveur où la fonction de suivi s'effectue.  
  
5.  Vous pouvez spécifier en option comment le serveur doit gérer les fichiers de substitution :  
  
    -   Sélectionnez **Charger tous les fichiers de substitution en séquence sans invite** pour charger automatiquement les fichiers de substitution pendant la relecture.  
  
    -   Sélectionnez **Demander confirmation avant le chargement des fichiers de substitution** pour contrôler le chargement des fichiers de substitution pendant la relecture.  
  
    -   Sélectionnez **Ne jamais charger les fichiers de substitution suivants** pour relire les fichiers un par un.  
  
6.  Vous pouvez éventuellement définir les options suivantes :  
  
    -   **Nombre par défaut de threads de relecture** contrôle le nombre de threads de processeurs à utiliser pendant la relecture. Un nombre de threads élevé accélère la relecture, mais dégrade les performances du serveur. La valeur recommandée est **4**. Le tableau suivant répertorie les options disponibles :  
  
        |Valeur|Description|  
        |-----------|-----------------|  
        |**2**|Valeur minimale. Utilisez deux threads pour la relecture.|  
        |**4**|Valeur par défaut.|  
        |**255**|Valeur maximale. Une valeur maximale risque de nuire aux performances d'autres processus.|  
  
    -   L’option **Délai d’attente du moniteur d’intégrité par défaut (sec)** définit la durée maximale, en secondes, pendant laquelle un thread peut bloquer un autre processus. Le tableau suivant indique les valeurs possibles.  
  
        |Valeur|Description|  
        |-----------|-----------------|  
        |**0**|Valeur minimale. **0** signifie que [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] n’arrêtera jamais un processus de blocage.|  
        |**3600**|Valeur par défaut. Autorise les processus de blocage dont la durée n’est pas supérieure à **3600** secondes (une heure).|  
        |**86400**|Valeur maximale. Autorise les processus de blocage dont la durée n’est pas supérieure à **86400** secondes (un jour).|  
  
    -   L’option **Intervalle d’interrogation du moniteur d’intégrité par défaut (s)** définit la fréquence d’interrogation des threads de relecture des processus de blocage. Le tableau suivant indique les valeurs possibles.  
  
        |Valeur|Description|  
        |-----------|-----------------|  
        |**1**|Valeur minimale. **1[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] signifie que ** interroge les processus de blocage une fois par seconde.|  
        |**60**|Valeur par défaut. Interroge les processus de blocage une fois par minute.|  
        |**86400**|Valeur maximale. Interroge les processus de blocage une fois toutes les **86400** secondes (une fois par jour).|  
  
## Voir aussi  
 [Définir les valeurs par défaut de l’affichage des traces &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  