---
title: "Principaux (moteur de base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "01/09/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.roleproperties.selectroll.f1"
  - "sql13.swb.databaseuser.permissions.user.f1--May use common.permissions"
helpviewer_keywords: 
  - "certificats [SQL Server], principaux"
  - "rôles [SQL Server], principaux"
  - "autorisations [SQL Server], principaux"
  - "##MS_SQLAuthenticatorCertificate##"
  - "principaux [SQL Server]"
  - "##MS_SQLResourceSigningCertificate##"
  - "groupes [SQL Server], principaux"
  - "##MS_AgentSigningCertificate##"
  - "authentification [SQL Server], principaux"
  - "schémas [SQL Server], principaux"
  - "principaux [SQL Server],à propos des principaux"
  - "sécurité [SQL Server], principaux"
  - "utilisateurs [SQL Server], principaux"
  - "##MS_SQLReplicationSigningCertificate##"
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
caps.latest.revision: 57
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 55
---
# Principaux (moteur de base de donn&#233;es)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../../includes/tsql-appliesto-ss2008-all-md.md)]

  Les*principaux* sont des entités qui peuvent demander des ressources [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Comme les autres composants du modèle d'autorisation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , les principaux peuvent être ordonnés de façon hiérarchique. Le champ d'influence d'un principal dépend de l'étendue de sa définition : Windows, serveur, base de données, et du fait qu'il est indivisible ou qu'il s'agit d'une collection. Une connexion Windows est un exemple de principal indivisible et un groupe Windows est un exemple de principal constituant une collection. Chaque principal a un identificateur de sécurité (SID).  
  
 **Principaux au niveau de Windows**  
  
-   Connexion à un domaine Windows  
  
-   Connexion locale Windows  
  
 **Principaux** **au niveau de****SQL Server**  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connexion  
  
-   Rôle serveur  
  
 **Principaux au niveau des bases de données**  
  
-   Utilisateur de base de données  
  
-   Rôle de base de données  
  
-   Rôle d'application  
  
## La connexion SQL Server sa  
 La connexion sa [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est un principal au niveau du serveur. Par défaut, elle est créée lorsqu'une instance est installée. À compter de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], la base de données par défaut de sa est MASTER. Il s'agit là d'une différence par rapport aux versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## Rôle de base de données public  
 Chaque utilisateur de base de données appartient au rôle de base de données public. Quand des autorisations spécifiques sur un élément sécurisable n’ont pas été accordées ni refusées à un utilisateur, celui-ci hérite des autorisations accordées à public sur cet élément sécurisable.  
  
## INFORMATION_SCHEMA et sys  
 Chaque base de données inclut deux entités qui apparaissent comme des utilisateurs dans des affichages catalogue : INFORMATION_SCHEMA et sys. Ces entités sont requises par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ce ne sont pas des principaux et ils ne peuvent être ni modifiés, ni supprimés.  
  
## Connexions SQL Server basées sur des certificats  
 Les principaux de serveur compris entre deux signes dièse (##) sont destinés uniquement à une utilisation système interne. Les principaux suivants sont créés à partir de certificats lors de l'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ; ils ne doivent pas être supprimés.  
  
-   \##MS_SQLResourceSigningCertificate##  
  
-   \##MS_SQLReplicationSigningCertificate##  
  
-   \##MS_SQLAuthenticatorCertificate##  
  
-   \##MS_AgentSigningCertificate##  
  
-   \##MS_PolicyEventProcessingLogin##  
  
-   \##MS_PolicySigningCertificate##  
  
-   \##MS_PolicyTsqlExecutionLogin##  
  
## Utilisateur invité  
 Chaque base de données inclut un **invité**. Les autorisations accordées à l'utilisateur **invité** sont héritées par les utilisateurs qui ont accès à la base de données, mais n'ont pas de compte d'utilisateur dans la base de données. L'utilisateur **invité** ne peut pas être supprimé, mais il est possible de le désactiver en supprimant son autorisation **CONNECT** . L’autorisation **CONNECT** peut être supprimée en exécutant l’instruction `REVOKE CONNECT FROM GUEST` dans n’importe quelle base de données différente des bases de données MASTER ou tempdb.  
  
## Client et serveur de base de données  
 Par définition, un client et un serveur de base de données sont des principaux de sécurité et peuvent être sécurisés. Ces entités peuvent être authentifiées mutuellement avant qu'une connexion réseau sécurisée soit établie. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge le protocole d'authentification [Kerberos](http://go.microsoft.com/fwlink/?LinkId=100758) , qui définit comment les clients interagissent avec un service d'authentification réseau.  
  
## Tâches associées  
 Pour plus d’informations sur la conception d’un système d’autorisations, consultez [Getting Started with Database Engine Permissions](../../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).  
  
 Les rubriques suivantes sont incluses dans cette section de la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   [Rubriques de procédures relatives à la gestion des connexions, des utilisateurs et des schémas](../../../relational-databases/security/authentication-access/managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [Rôles de niveau serveur](../../../relational-databases/security/authentication-access/server-level-roles.md)  
  
-   [Rôles au niveau de la base de données](../../../relational-databases/security/authentication-access/database-level-roles.md)  
  
-   [Rôles d'applications](../../../relational-databases/security/authentication-access/application-roles.md)  
  
## Voir aussi  
 [Sécurisation de SQL Server](../../../relational-databases/security/securing-sql-server.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.sql_logins &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-sql-logins-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [Rôles de niveau serveur](../../../relational-databases/security/authentication-access/server-level-roles.md)   
 [Rôles au niveau de la base de données](../../../relational-databases/security/authentication-access/database-level-roles.md)  
  
  