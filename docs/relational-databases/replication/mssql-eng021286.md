---
title: "MSSQL_ENG021286 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG021286 (erreur)"
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# MSSQL_ENG021286
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21286|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|La table de conflits '%1!' n'existe pas.|  
  
## Explication  
 Cette erreur est générée si la table de conflits pour un article répertorié dans [sysmergearticles & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-tables/sysmergearticles-transact-sql.md) n’existe pas réellement. Cette erreur peut se produire lorsque vous tentez d'ajouter ou de supprimer une colonne d'une table publiée pour la réplication de fusion.  
  
## Action de l'utilisateur  
 Exécutez [DBCC CHECKDB & #40 ; Transact-SQL & #41 ;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) sur la base de données avec la table de conflits manquante pour vérifier il n’existe aucun problème de cohérence des données.  
  
 Si la table de conflits n'existe pas sur un Abonné, supprimez l'abonnement puis recréez-le. Si la table des conflits n'existe pas sur un serveur de publication, supprimez tous les abonnement, supprimez la publication puis recréez la publication et tous les abonnements. Pour plus d’informations, consultez [publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md) et [s’abonner aux Publications](../../relational-databases/replication/subscribe-to-publications.md).  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  