---
title: "Actions courantes n&#233;cessitant une sauvegarde mise &#224; jour | Microsoft Docs"
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
  - "récupération [réplication SQL Server], actions nécessitant une sauvegarde"
  - "restauration [réplication SQL Server], actions nécessitant une sauvegarde"
  - "sauvegardes [réplication SQL Server], actions nécessitant une sauvegarde"
ms.assetid: a5975bf4-183e-42e3-b7d1-ad02f89d2e1d
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# Actions courantes n&#233;cessitant une sauvegarde mise &#224; jour
  Si vous effectuez des sauvegardes régulières des journaux, toutes les modifications liées à la réplication doivent être capturées dans les sauvegardes des journaux. Si vous n’effectuez des sauvegardes de journaux, effectuez une sauvegarde de la publication, la distribution, l’abonnement, **msdb**, et **master** bases de données après avoir apporté des modifications à votre schéma de réplication ou de la topologie.  
  
## Base de données de publication  
 Sauvegardez la base de données de publication après avoir :  
  
-   créé de nouvelles de publications ;  
  
-   modifié toute propriété de publication, notamment le filtrage ;  
  
-   ajouté des articles à une publication existante ;  
  
-   réalisé une réinitialisation des abonnements au niveau de la publication ;  
  
-   effectué une modification de schéma sur une table publiée ;  
  
-   Exécution de l’exécution du script de la demande avec [sp_addscriptexec & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md).  
  
-   modifié toute propriété d'article ;  
  
-   supprimé une publication ;  
  
-   supprimé un article ;  
  
-   désactivé la réplication.  
  
## Base de données de distribution  
 Sauvegardez la base de données de distribution après avoir :  
  
-   créé ou modifié des profils d'Agent de réplication ;  
  
-   modifié les paramètres de profils d'Agent de réplication ;  
  
-   modifié les propriétés d'Agent de réplication (notamment les planifications) d'abonnements envoyés.  
  
-   Une nouvelle plage d'identité est assignée par la fonctionnalité de gestion des plages d'identité.  
  
## Base de données d'abonnement  
 Sauvegardez la base de données d'abonnement après avoir :  
  
-   modifié toute propriété d'abonnement ;  
  
-   modifié la priorité d'un abonnement de fusion sur le serveur de publication ;  
  
-   supprimé un abonnement ;  
  
-   désactivé la réplication.  
  
## Base de données msdb  
 Sauvegarde le **msdb** base de données système sur le nœud approprié après :  
  
-   activé ou désactivé la réplication ;  
  
-   ajouté ou supprimé une base de données de distribution (sur le serveur de distribution) ;  
  
-   activé ou désactivé une base de données destinée à être publiée (sur le serveur de publication) ;  
  
-   créé ou modifié des profils d'Agent de réplication (sur le serveur de distribution) ;  
  
-   modifié des paramètres de profils d'Agent de réplication (sur le serveur de distribution) ;  
  
-   modifié les propriétés d'Agent de réplication (notamment les planifications) d'un abonnement envoyé (sur le serveur de distribution) ;  
  
-   modifié les propriétés d'Agent de réplication (notamment les planifications) d'un abonnement extrait (sur l'Abonné) ;  
  
-   créé un package DTS associé à une publication transactionnelle qui utilise des abonnements transformables (sur le serveur de distribution et sur le serveur de publication) ;  
  
-   ajouté ou supprimé un abonnement transformable (sur le serveur de distribution et sur le serveur de publication) ;  
  
## Base de données master  
 Sauvegarde le **master** base de données système sur le nœud approprié après :  
  
-   activé ou désactivé la réplication ;  
  
-   ajouté ou supprimé une base de données de distribution (sur le serveur de distribution) ;  
  
-   activé ou désactivé une base de données destinée à être publiée (sur le serveur de publication) ;  
  
-   ajouté la première publication, ou supprimé la dernière, dans une base de données (sur le serveur de publication) ;  
  
-   ajouté le premier abonnement, ou supprimé le dernier, dans une base de données (sur l'Abonné) ;  
  
-   activé ou désactivé un serveur de publication sur un serveur de publication de distribution (sur le serveur de publication et le serveur de distribution).  
  
## Voir aussi  
 [Sauvegarde et restauration des bases de données SQL Server](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Sauvegarder et restaurer des bases de données répliquées](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)  
  
  