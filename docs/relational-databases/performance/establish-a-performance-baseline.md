---
title: "&#201;tablir un niveau de r&#233;f&#233;rence des performances | Microsoft Docs"
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
  - "performances de base de données [SQL Server], lignes de base"
  - "analyse des performances [SQL Server], lignes de base"
  - "paramétrage des bases de données [SQL Server], lignes de base"
  - "performances du serveur [SQL Server], lignes de base"
  - "performances [SQL Server], lignes de base"
  - "niveau de référence des performances [SQL Server]"
  - "mesures des statistiques de référence [SQL Server]"
  - "analyse des performances du serveur [SQL Server], mise en place de la ligne de base"
  - "surveillance de la base de données [SQL Server], lignes de base"
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# &#201;tablir un niveau de r&#233;f&#233;rence des performances
  Pour déterminer si votre système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assure des performances optimales, mesurez les performances à intervalles réguliers, même en l'absence de problèmes, pour établir un niveau de référence des performances du serveur. Comparez chaque nouvel ensemble de mesures à ceux réalisés précédemment.  
  
 Les éléments suivants ont une influence sur les performances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   ressources système (matériel) ;  
  
-   architecture réseau ;  
  
-   système d'exploitation ;  
  
-   applications de base de données ;  
  
-   applications clientes.  
  
 Au minimum, vous devez effectuer des mesures de niveau de référence pour déterminer :  
  
-   les heures de pointe et les heures creuses d'exploitation ;  
  
-   les temps de réponse des requêtes de production et des commandes de traitement par lots ;  
  
-   les temps de sauvegarde et de restauration de la base de données.  
  
 Après avoir établi le niveau de référence des performances, comparez vos statistiques aux performances actuelles du serveur. Toute valeur très supérieure ou très inférieure à votre niveau de référence doit donner lieu à un examen approfondi. Elle peut indiquer la nécessité d'optimiser ou de reconfigurer certains points. Par exemple, si le temps nécessaire à l'exécution d'un ensemble de requêtes augmente, examinez les requêtes en question pour déterminer si vous pouvez les réécrire ou si vous devez ajouter des colonnes de statistiques ou de nouveaux index.  
  
## Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  