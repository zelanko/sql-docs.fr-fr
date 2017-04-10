---
title: "Afficher un rapport de jeu d&#39;&#233;l&#233;ments de collecte (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.dc.reporthistory.calendar.f1"
helpviewer_keywords: 
  - "jeux d’éléments de collecte [SQL Server], affichage des rapports"
  - "rapports [SQL Server], affichage de jeux d’éléments de collecte"
ms.assetid: c3b1e791-9aa1-4bba-9622-4954568e1820
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Afficher un rapport de jeu d&#39;&#233;l&#233;ments de collecte (SQL Server Management Studio)
  Après avoir configuré l'entrepôt de données de gestion, vous pouvez afficher un rapport sur un jeu d'éléments de collecte dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Des rapports sont fournis pour les jeux d'éléments de collecte de données système installés pendant l'installation. Les rapports proposés sont les suivants :  
  
-   Résumé sur l'utilisation du disque  
  
-   Historique des statistiques sur les requêtes  
  
-   Historique de l'activité du serveur  
  
 Cette procédure affiche le rapport pour le jeu d’éléments de collecte **Utilisation du disque**. Vous pouvez suivre la même procédure générale pour afficher les rapports des autres jeux d'éléments de collecte de données système.  
  
### Pour afficher un rapport de jeu d'éléments de collecte  
  
1.  Les tables d'un rapport sont créées lorsque les données collectées sont téléchargées pour la première fois. Si vous essayez de consulter un rapport avant ce premier téléchargement, une erreur se produit et aucun rapport n'est affiché. Pour charger des données pour le jeu d’éléments de collecte Utilisation du disque, dans l’Explorateur d’objets, développez le dossier **Gestion**, **Collecte de données**, puis **Jeux d’éléments de collecte de données système**, cliquez avec le bouton droit sur le jeu d’éléments de collecte **Utilisation du disque** et cliquez enfin sur **Collecter et télécharger maintenant**.  
  
2.  Pour afficher le rapport, dans l’Explorateur d’objets, développez le dossier **Gestion**, cliquez avec le bouton droit sur **Collecte de données**, pointez sur **Rapports**, sur **Entrepôt de données de gestion**, puis cliquez sur **Résumé sur l’utilisation du disque**.  
  
    > [!NOTE]  
    >  Certains rapports peuvent afficher un bouton Calendrier sous la chronologie de collecte de données. Cliquez sur ce bouton pour accéder au **Calendrier des rapports de collecte de données**.  
  
#### Calendrier des rapports de collecte de données  
 Utilisez cette boîte de dialogue pour spécifier la date de début, l'heure de début et la durée des données pour lesquelles vous voulez créer un rapport. Par exemple, vous pouvez générer un rapport sur l'activité d'utilisation du disque d'un serveur pour une période spécifique de 12 heures mercredi dernier.  
  
 **Date de début**  
 Entrez une date de début pour les données du rapport ou sélectionnez-la dans le calendrier.  
  
 **Heure de début**  
 Entrez une heure de début pour les données du rapport ou spécifiez-la en cliquant sur les flèches.  
  
 **Duration**  
 Spécifiez la plage de temps à inclure dans le rapport. La valeur par défaut est 240 minutes. Les valeurs possibles pour la sélection sont 15 minutes, 60 minutes, 240 minutes (4 heures), 720 minutes (12 heures) et 1440 minutes (24 heures).  
  
## Voir aussi  
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)   
 [Rapports personnalisés dans Management Studio](../../ssms/object/custom-reports-in-management-studio.md)   
 [Configurer l’entrepôt de données de gestion &#40;SQL Server Management Studio&#41;](../../relational-databases/data-collection/configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  