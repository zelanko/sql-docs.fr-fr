---
title: "Enregistrer s&#233;par&#233;ment des &#233;v&#233;nements Showplan XML (G&#233;n&#233;rateur de profils SQL Server) | Microsoft Docs"
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
  - "événements Showplan XML"
  - "enregistrement des événements Showplan XML"
  - "événements [SQL Server], Showplan XML"
ms.assetid: 33320a7a-36e8-401c-876d-5b82c49abd85
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 25
---
# Enregistrer s&#233;par&#233;ment des &#233;v&#233;nements Showplan XML (G&#233;n&#233;rateur de profils SQL Server)
  Cette rubrique explique comment enregistrer des événements **Showplan XML** qui sont capturés dans des traces dans des fichiers .SQLPlan différents avec le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Vous pouvez ouvrir les fichiers des événements **Showplan XML** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ce qui vous permet de voir le plan d'exécution graphique pour chaque événement.  
  
### Pour enregistrer séparément des événements Showplan XML  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de SQL Server.  
  
     La boîte de dialogue **Propriétés de la trace**apparaît.  
  
    > [!NOTE]  
    >  Si la case **Démarrer le suivi juste après avoir établi la connexion**est cochée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et le suivi se lance. Pour désactiver ce paramètre, dans le menu **Outils,**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la zone **Nom de la trace** de la boîte de dialogue **Propriétés de la trace** , entrez le nom de la trace.  
  
3.  Dans la liste **Utiliser le modèle** , sélectionnez un modèle de trace comme base ou sélectionnez **Vide** si vous ne souhaitez pas utiliser de modèle.  
  
4.  Procédez de l'une des manières suivantes :  
  
    -   Activez la case à cocher**Enregistrer dans le fichier** pour capturer la trace dans un fichier. Spécifiez une valeur dans **Définir la taille de fichier maximale**. Au besoin, activez les cases à cocher **Activer la substitution de fichier** et **Le serveur traite les données de trace** .  
  
    -   Activez la case à cocher**Enregistrer dans la table** pour capturer la trace dans une table de base de données. Éventuellement, spécifiez une valeur dans **Définir le nombre de lignes maximal**.  
  
5.  Le cas échéant, activez la case à cocher **Activer l'heure d'arrêt de la trace** et indiquez une date et une heure d'arrêt.  
  
6.  Cliquez sur l’onglet **Sélection des événements**.  
  
7.  Dans la zone **Événements,**développez la catégorie d'événements **Performance,**puis activez la case à cocher **Showplan XML**. Si la catégorie d'événements **Performance** n'est pas visible, activez la case à cocher **Afficher tous les événements** pour l'afficher.  
  
     La boîte de dialogue **Paramètres d’extraction des événements** est ajoutée à la boîte de dialogue **Propriétés de la trace**.  
  
8.  Dans le menu **Paramètres d’extraction des événements**, cliquez sur **Enregistrer les événements Showplan XML séparément**.  
  
9. Dans la boîte de dialogue **Enregistrer sous** , entrez le nom du fichier dans lequel vous souhaitez stocker les événements **Showplan XML** .  
  
10. Cliquez sur **Tous les lots Showplan XML dans un seul fichier** pour enregistrer tous les événements **Showplan XML** dans un seul fichier XML ou cliquez sur **Chaque lot Showplan XML dans un fichier différent**pour créer un nouveau fichier XML pour chaque événement **Showplan XML** .  
  
11. Pour afficher le fichier d'événements **Showplan XML** dans SQL Server Management Studio, ouvrez le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Fichier**. Recherchez le répertoire où vous avez enregistré le ou les fichiers d'événements **Showplan XML** pour en sélectionner un et l'ouvrir. Les fichiers d'événements**Showplan XML** ont l'extension .SQLPlan.  
  
## Voir aussi  
 [Analyser des requêtes avec des résultats SHOWPLAN dans SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)  
  
  