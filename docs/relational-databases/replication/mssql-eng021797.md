---
title: "MSSQL_ENG021797 | Microsoft Docs"
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
  - "MSSQL_ENG021797 (erreur)"
ms.assetid: 54d83a1e-43fd-449c-a2b2-fdda2609a534
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG021797
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21797|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|'%s' doit être une connexion Windows valide sous la forme 'MACHINE\Login' ou 'DOMAIN\Login'. Consultez la documentation de '%s'.|  
  
## Explication  
 Cette erreur est générée par les procédures stockées de réplication suivants si la valeur spécifiée pour le **@job_login** paramètre est null ou non valide. Cette erreur peut se produire si un membre de la **db_owner** rôle fixe de base de données exécute les scripts des versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le modèle de sécurité a changé dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et ces scripts doivent être mis à jour.  
  
-   [sp_addlogreader_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
-   [sp_addqreader_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)  
  
-   [sp_addpublication_snapshot & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  
  
-   [sp_addpullsubscription_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)  
  
-   [sp_addpullsubscription_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)  
  
-   [sp_addmergepushsubscription_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md)  
  
-   [sp_addmergepullsubscription_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)  
  
 Ces procédures stockées peuvent être exécutées par un membre de la **sysadmin** rôle serveur fixe sur le serveur approprié ou un membre de la **db_owner** rôle fixe de base de données dans la base de données appropriée. Les procédures stockées créent chacune un travail d'Agent et vous permettent de spécifier le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] sous lequel l'Agent s'exécute. Pour les utilisateurs dans le **sysadmin** rôle, des travaux de l’agent créés implicitement même si un compte Windows n’est pas spécifié (si un compte est spécifié, il doit être valide) ; agents s’exécutent dans le contexte de le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte de service de l’Agent sur le serveur approprié. Bien que ce compte ne soit pas nécessaire, il est recommandé de spécifier un compte distinct pour les Agents. Pour plus d'informations, voir [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Action de l'utilisateur  
 Assurez-vous de vous spécifiez un compte Windows valide pour le **@job_login** paramètre de chaque procédure. Si vous avez des scritps de réplication provenant de versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mettez-les à jour pour qu'ils incluent les procédures stockées et les paramètres requis par [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Pour plus d’informations, consultez [mettre à niveau les Scripts de réplication & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../relational-databases/replication/administration/upgrade-replication-scripts-replication-transact-sql-programming.md).  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  