---
title: "MSSQL_REPL020011 | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_REPL020011 (erreur)"
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_REPL020011
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|20011|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Le processus n'a pas pu exécuter '%1' sur '%2'.|  
  
## Explication  
 Cette erreur peut survenir dans un certain nombre de cas au cours de traitement, par exemple lorsque l’Agent de lecture du journal s’exécute la réplication transactionnelle **sp_replcmds** (le processus n’a pas pu exécuter 'sp_replcmds' sur \< nom_serveur>) ou **sp_repldone** (le processus Impossible d’exécuter 'sp_repldone' sur \< nom_serveur>).  
  
## Action de l'utilisateur  
 Si cette erreur est générée dans une base de données que vous venez de restaurer à partir d’une sauvegarde, assurez-vous de vous avez suivi les étapes décrites dans la documentation de sauvegarde et de restauration, notamment l’exécution **sp_replrestart** si nécessaire. Pour plus d’informations, consultez [stratégies de sauvegarde et restauration de capture instantanée et la réplication transactionnelle](../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
 Cette erreur est une erreur de traitement interne et, si elle est signalée dans d'autres circonstances que celle d'une restauration, elle indique généralement que la réplication doit être supprimée et reconfigurée. Si vous ne parvenez pas à supprimer la réplication, contactez le support technique pour obtenir de l'aide.  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [sp_replcmds & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)  
  
  