---
title: "MSSQL_ENG014121 | Microsoft Docs"
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
  - "MSSQL_ENG014121 (erreur)"
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# MSSQL_ENG014121
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14121|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de supprimer le distributeur '%s'. Des bases de données de distribution sont associées à ce distributeur.|  
  
## Explication  
 Une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est configurée en tant que serveur de distribution ne peut pas être supprimée du rôle Serveur de distribution car il y a des bases de données de distribution associées à l'instance. Cette erreur se produit si vous tentez de supprimer une base de données de distribution qui est associée à un ou plusieurs serveurs de publication.  
  
## Action de l'utilisateur  
 Pour trouver les noms des éditeurs et des bases de données de distribution associées à ce serveur de distribution, exécutez [sp_helpdistpublisher & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md) à partir d’une base de données sur le serveur de distribution.  
  
 Exécutez [sp_dropdistributiondb & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md) pour les bases de données de distribution associées à ce serveur de distribution. Quand toutes les associations de base de données de distribution sont supprimées, vous pouvez désactiver la distribution.  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)  
  
  