---
title: "MSSQL_ENG021331 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG021331 (erreur)"
ms.assetid: 9acd75d9-fda1-44cd-ba17-20295ad53ea0
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_ENG021331
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21331|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de copier le fichier de script utilisateur vers le distributeur.(%1!)|  
  
## Explication  
 Cette erreur peut se produire lorsqu'un abonnement est initialisé manuellement et que les scripts générés par la réplication ou spécifiés dans une commande de réplication ne peuvent pas être enregistrés dans le répertoire spécifié. L'erreur peut être due à un problème d'autorisations : lorsqu'un abonnement est initialisé sans utiliser d'instantané, le compte sous lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute sur le serveur de publication doit disposer d'autorisations en écriture sur le dossier d'instantané hébergé sur le serveur de distribution.  
  
## Action de l'utilisateur  
 Vérifiez que le chemin d'accès correct a été spécifié pour le dossier d'instantané et que le compte sous lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute sur le serveur de publication a des autorisations suffisantes.  
  
## Voir aussi  
 [Spécifier l’emplacement par défaut des instantanés & #40 ; SQL Server Management Studio & #41 ;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Initialiser un abonnement transactionnel sans instantané](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  