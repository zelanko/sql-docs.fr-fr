---
title: "MSSQL_ENG021798 | Microsoft Docs"
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
  - "MSSQL_ENG021798 (erreur)"
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_ENG021798
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21798|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Le travail de l'Agent « %1!s! » doit être ajouté à l'aide de « %2!s! » avant de continuer. Consultez la documentation de '%s'.|  
  
## Explication  
 Pour créer une publication, vous devez être un membre de la **sysadmin** rôle serveur fixe sur le serveur de publication ou un membre de la **db_owner** rôle fixe de base de données dans la base de données de publication. Si vous êtes un membre de la **db_owner** rôle, cette erreur est déclenchée si :  
  
-   Vous exécutez des scripts à partir de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Le modèle de sécurité a changé dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et ces scripts doivent être mis à jour.  
  
-   La procédure stockée **sp_addpublication** est exécuté avant l’exécution de [sp_addlogreader_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Ceci s'applique à toutes les publications transactionnelles.  
  
-   La procédure stockée **sp_addpublication** est exécuté avant l’exécution de [sp_addqreader_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md). Cela s’applique aux publications transactionnelles qui sont activées pour les abonnements mis à jour en file d’attente (la valeur TRUE pour le **@allow_queued_tran** paramètre de **sp_addpublication**).  
  
 Les procédures stockées **sp_addlogreader_agent** et **sp_addqreader_agent** créent chacune un travail d’agent et vous permet de spécifier le [!INCLUDE[msCoName](../../includes/msconame-md.md)] du compte Windows sous lequel s’exécute l’agent. Pour les utilisateurs dans le **sysadmin** rôle, des travaux de l’agent créés implicitement si **sp_addlogreader_agent** et **sp_addqreader_agent** ne sont pas exécutées ; agents s’exécutent dans le contexte de le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte de service de l’Agent sur le serveur de distribution. Bien que **sp_addlogreader_agent** et **sp_addqreader_agent** ne sont pas requis pour les utilisateurs dans le **sysadmin** rôle, il est une meilleure pratique de sécurité pour spécifier un compte distinct pour les agents. Pour plus d'informations, voir [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Action de l'utilisateur  
 Veillez à exécuter les procédures dans le bon ordre. Pour plus d'informations, voir [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md). Si vous avez des scripts de réplication provenant de versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mettez-les à jour pour qu'ils incluent les procédures stockées et les paramètres requis par [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures. Pour plus d’informations, consultez [mettre à niveau les Scripts de réplication & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md).  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  