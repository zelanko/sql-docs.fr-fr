---
title: "MSSQL_ENG004929 | Microsoft Docs"
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
  - "MSSQL_ENG004929 (erreur)"
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG004929
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|4929|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de modifier %1! '%2!' parce qu'elle est en cours d'édition pour la réplication.|  
  
## Explication  
 Cette erreur se produit généralement lorsque vous tentez de supprimer la contrainte de clé primaire d'une table publiée pour la réplication transactionnelle. Comme la réplication transactionnelle nécessite une clé primaire pour chaque table publiée, la contrainte ne peut pas être supprimée.  
  
## Action de l'utilisateur  
 Pour supprimer la contrainte, commencez par supprimer l'article associé à la table. Pour plus d’informations, consultez [Ajouter et supprimer des Articles de Publications existantes](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md). Si cette erreur se produit dans une base de données n’est pas répliquée, exécutez [sp_removedbreplication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) Pour garantir que les objets dans la base de données ne sont pas marqués comme étant répliqués.  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  