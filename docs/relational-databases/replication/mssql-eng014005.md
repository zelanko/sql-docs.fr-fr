---
title: "MSSQL_ENG014005 | Microsoft Docs"
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
  - "MSSQL_ENG014005 (erreur)"
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# MSSQL_ENG014005
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14005|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de supprimer la publication.. Il existe un abonnement.|  
  
## Explication  
 Vous avez tenté de supprimer une publication qui a un ou plusieurs abonnements associés. Une publication peut être supprimée seulement s'il n'y a pas d'abonnements associés.  
  
## Action de l'utilisateur  
 Supprimez les abonnements avant de supprimer la publication. Si vous utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour supprimer la publication, vous pouvez choisir de supprimer automatiquement tous les abonnements associés avant de supprimer la publication. Si vous utilisez des procédures stockées, vous devez d'abord explicitement supprimer les abonnements. Pour plus d’informations, consultez [Supprimer un abonnement Push](../../relational-databases/replication/delete-a-push-subscription.md) et [Supprimer un abonnement extrait](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 S'il semble ne pas exister d'abonnements pour la publication ou si vous voyez cette erreur quand vous créez une publication, il est possible qu'un abonnement antérieur n'ait pas été complètement nettoyé quand il a été supprimé. Exécutez [sp_removedbreplication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) sur la base de données pour supprimer tous les objets et paramètres liés à la réplication.  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  