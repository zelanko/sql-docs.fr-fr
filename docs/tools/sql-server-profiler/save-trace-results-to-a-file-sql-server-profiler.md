---
title: "Enregistrer des r&#233;sultats d&#39;une trace dans un fichier (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "enregistrement des traces"
  - "traces [SQL Server], enregistrement"
ms.assetid: ac528747-0c19-4f3d-96f5-44c762a4abed
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# Enregistrer des r&#233;sultats d&#39;une trace dans un fichier (SQL Server Profiler)
  Cette rubrique explique comment enregistrer les résultats d'une trace dans un fichier en utilisant le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### Pour enregistrer les résultats d'une trace dans un fichier  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     La boîte de dialogue **Propriétés de la trace**apparaît.  
  
    > [!NOTE]  
    >  Si la case **Démarrer le suivi juste après avoir établi la connexion**est cochée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et le suivi se lance. Pour désactiver ce paramètre, dans le menu **Outils**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la zone **Nom de la trace**, tapez un nom destiné à la trace.  
  
3.  Cochez la case **Enregistrer dans le fichier**.  
  
     La boîte de dialogue **Enregistrer sous** s’affiche.  
  
4.  Spécifiez un chemin et un nom de fichier dans la boîte de dialogue **Enregistrer sous**. Cliquez sur **Enregistrer**.  
  
    > [!NOTE]  
    >  Vérifiez que le service SQL Server dispose des autorisations suffisantes pour écrire dans un fichier dans le répertoire défini.  
  
5.  Dans la boîte de dialogue **Propriétés de la trace**, entrez la taille de fichier maximale dans la zone de texte **Définir la taille de fichier maximale (Mo)**. La valeur par défaut est 5 mégaoctets (Mo).  
  
6.  Vous pouvez également définir les options facultatives suivantes :  
  
    -   Cochez la case **Activer la substitution de fichier** pour que [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] crée des fichiers pour les données de trace lorsque la limite de taille de fichier maximale est atteinte. Cette option est activée par défaut.  
  
    -   Cochez la case **Le serveur traite les données de trace** pour que le serveur enregistre chaque événement de trace.  
  
        > [!NOTE]  
        >  Lorsque l’option **Le serveur traite les données de trace** est désactivée, le serveur n’enregistre pas les événements si cette opération dégrade sensiblement les performances.  
  
## Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  