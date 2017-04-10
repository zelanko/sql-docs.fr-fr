---
title: "Enregistrer des r&#233;sultats d&#39;une trace dans une table (SQL Server Profiler) | Microsoft Docs"
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
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Enregistrer des r&#233;sultats d&#39;une trace dans une table (SQL Server Profiler)
  Cette rubrique explique comment enregistrer les résultats d'une trace dans une table de base de données à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### Pour enregistrer les résultats d'une trace dans une table  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouvelle trace**, puis connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     La boîte de dialogue **Propriétés de la trace**apparaît.  
  
    > [!NOTE]  
    >  Si la case **Démarrer le suivi juste après avoir établi la connexion**est cochée, la boîte de dialogue **Propriétés de la trace**ne s’affiche pas et le suivi se lance. Pour désactiver ce paramètre, dans le menu **Outils**, cliquez sur **Options**et désactivez la case à cocher **Démarrer le suivi juste après avoir établi la connexion** .  
  
2.  Dans la zone **Nom de la trace**, entrez le nom de la trace, puis cliquez sur **Enregistrer dans la table**.  
  
3.  Dans la boîte de dialogue **Se connecter au serveur**, connectez-vous à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contiendra la table.  
  
4.  Dans la boîte de dialogue **Table de destination**, sélectionnez le nom d’une base de données dans la liste **Base de données**.  
  
5.  Dans la liste **Propriétaire**, sélectionnez le propriétaire de la trace.  
  
6.  Dans la liste **Table**, tapez ou sélectionnez le nom de la table dans laquelle seront enregistrés les résultats de la trace. Cliquez sur **OK.**  
  
7.  Dans la boîte de dialogue **Propriétés de la trace**, cochez la case **Définir le nombre de lignes maximal (en milliers)** pour définir le nombre maximal de lignes à enregistrer.  
  
## Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  