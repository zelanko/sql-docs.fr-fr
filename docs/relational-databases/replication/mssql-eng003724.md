---
title: "MSSQL_ENG003724 | Microsoft Docs"
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
  - "MSSQL_ENG003724 (erreur)"
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# MSSQL_ENG003724
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3724|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de %1! le %2! '%3!' parce qu'il est utilisé pour la réplication.|  
  
## Explication  
 Lorsque les objets dans une base de données sont répliquées, ils sont marqués comme étant répliqués dans la table système **sysarticles** (pour les publications transactionnelles et de capture instantanée) ou **sysmergearticles** (pour les publications de fusion). Si vous tentez de supprimer un objet répliqué, cette erreur est générée.  
  
## Action de l'utilisateur  
 Vérifiez que l'objet de base de données n'est pas répliqué avant d'essayer de le supprimer. Exemple :  
  
-   Si l'erreur se produit dans la base de données de publication, supprimez l'article de la publication avant de supprimer l'objet. Pour plus d’informations, consultez [Ajouter et supprimer des Articles de Publications existantes](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
-   Si l'erreur se produit dans la base de données d'abonnement, supprimez l'abonnement avant de supprimer l'objet. Pour plus d’informations, consultez la page [s’abonner aux Publications](../../relational-databases/replication/subscribe-to-publications.md). Dans le cas d'abonnements aux publications transactionnelles, il est possible de supprimer l'abonnement à un article individuel plutôt qu'à la publication complète. Pour plus d’informations, consultez [sp_dropsubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md).  
  
 Si cette erreur se produit dans une base de données n’est pas répliquée, exécutez [sp_removedbreplication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) Pour garantir que les objets dans la base de données ne sont pas marqués comme étant répliqués.  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  