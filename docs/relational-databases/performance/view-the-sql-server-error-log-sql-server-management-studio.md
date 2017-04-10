---
title: "Afficher le journal des erreurs SQL&#160;Server (SQL&#160;Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "07/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "affichage des journaux"
  - "affichage des journaux"
  - "erreurs [SQL Server], journaux"
  - "journaux [SQL Server], journaux d'erreurs SQL Server"
  - "journaux [SQL Server], affichage"
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
caps.latest.revision: 14
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 14
---
# Afficher le journal des erreurs SQL&#160;Server (SQL&#160;Server Management Studio)
  Le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient des événements définis par l’utilisateur et certains événements système utiles pour la résolution des problèmes. 
  

  ## Comment afficher les journaux
1.  Dans SSMS, sélectionnez **Explorateur d’objets**.

>Pour **ouvrir** l’Explorateur d’objets, vous pouvez utiliser le raccourci clavier **F8** ou cliquer sur Affichage > Explorateur d’objets dans le menu supérieur.![Explorateur d’objets](../../relational-databases/performance/media/object-explorer.png) 


2.  Dans **l’Explorateur d’objets**, connectez-vous à une instance de SQL Server et développez-la.
  
3.  Recherchez et développez la section **Gestion** (en supposant que vous disposez des autorisations nécessaires pour la voir).

4.  Cliquez avec le bouton droit sur **Journaux SQL Server**, sélectionnez Affichage, puis choisissez **Afficher le journal SQL Server**.
 ![Affichage du journal SQL Server dans SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5.  La visionneuse du fichier journal s’affiche (l’opération peut prendre une minute) avec une liste des journaux consultables.
  
6. Plusieurs personnes ont recommandé un billet utile de [MSSQLTips.com](https://www.mssqltips.com/), [Identify location of the SQL Server Error Log file](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/) (Identifier l’emplacement du fichier journal des erreurs de SQL Server). Ce site regorge d’excellentes informations formidables. Nous ne pouvons que vous conseiller d’aller y jeter un œil !
  
  