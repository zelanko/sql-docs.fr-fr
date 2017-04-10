---
title: "MSSQL_ENG020596 | Microsoft Docs"
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
  - "MSSQL_ENG020596 (erreur)"
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG020596
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|20596|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Seul '%1!' ou les membres de db_owner peuvent supprimer l'Agent anonyme.|  
  
## Explication  
 Vous ne disposez pas des autorisations suffisantes pour supprimer l'agent pour l'abonnement anonyme. Nom de connexion utilisé lors de l’appel [sp_dropanonymousagent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql.md) doit être un membre de la **sysadmin** rôle serveur fixe sur le serveur de distribution ou **db_owner** rôle fixe de base de données dans la base de données de distribution ou de l’utilisateur doit être celui qui a lancé la première exécution de l’agent.  
  
## Action de l'utilisateur  
 Connectez-vous avec les informations d’identification appropriées et d’exécuter **sp_dropanonymousagent**.  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  