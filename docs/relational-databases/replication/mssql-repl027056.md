---
title: "MSSQL_REPL027056 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_REPL027056 (erreur)"
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_REPL027056
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|27056|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Le processus de fusion n'a pas pu modifier l'historique de génération sur le '%1'. Lors de la résolution du problème, redémarrez la synchronisation avec un enregistrement d'historique détaillé et spécifiez un fichier de sortie dans lequel écrire.|  
  
## Explication  
 Cette erreur résulte généralement d'une contention dans les tables système de réplication de fusion devenues trop volumineuses. Une longue période de rétention de publication est souvent à l'origine d'une croissance excessive des tables système car les métadonnées doivent être stockées dans ces tables jusqu'à la fin de la période de rétention.  
  
## Action de l'utilisateur  
 **Pour résoudre ce problème :**  
  
1.  Diminuez la valeur de-**DownloadGenerationsPerBatch** et **- UploadGenerationsPerBatch** émettre des paramètres pour l’Agent de fusion permettre au traitement de continuer pendant que vous résolvez sous-jacent à l’origine de l’erreur. Les paramètres des agents peuvent être spécifiés dans des profils d'agent et sur la ligne de commande. Pour plus d'informations, consultez :  
  
    -   [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [Afficher et modifier les paramètres d’invite de l’Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [Concepts des exécutables de l’Agent réplication](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
2.  Spécifiez une période de rétention de publication la plus courte possible. Pour plus d'informations, voir [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
3.  Dans le cadre de la gestion de la réplication de fusion, contrôlez la croissance des tables système associées à la réplication de fusion : **MSmerge_contents**, **MSmerge_genhistory**, et **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, et **MSmerge_past_partition_mappings**. Réindexez périodiquement ces tables. Pour plus d’informations, consultez [réorganisation et reconstruction des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  