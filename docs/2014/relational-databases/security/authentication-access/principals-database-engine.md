---
title: Principaux (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectroll.f1
- sql12.swb.databaseuser.permissions.user.f1--May use common.permissions
helpviewer_keywords:
- certificates [SQL Server], principals
- roles [SQL Server], principals
- permissions [SQL Server], principals
- '##MS_SQLAuthenticatorCertificate##'
- principals [SQL Server]
- '##MS_SQLResourceSigningCertificate##'
- groups [SQL Server], principals
- '##MS_AgentSigningCertificate##'
- authentication [SQL Server], principals
- schemas [SQL Server], principals
- principals [SQL Server], about principals
- security [SQL Server], principals
- users [SQL Server], principals
- '##MS_SQLReplicationSigningCertificate##'
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 808c8516b3ed9e95ea4c724736461cb00923a7fb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85016236"
---
# <a name="principals-database-engine"></a>Principaux (moteur de base de données)
  Les*principaux* sont des entités qui peuvent demander des ressources [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Comme les autres composants du modèle d'autorisation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , les principaux peuvent être ordonnés de façon hiérarchique. Le champ d'influence d'un principal dépend de l'étendue de sa définition : Windows, serveur, base de données, et du fait qu'il est indivisible ou qu'il s'agit d'une collection. Une connexion Windows est un exemple de principal indivisible et un groupe Windows est un exemple de principal constituant une collection. Chaque principal a un identificateur de sécurité (SID).  
  
 **Principaux au niveau de Windows**  
  
-   Connexion à un domaine Windows  
  
-   Connexion locale Windows  
  
 **SQL Server** - **level** **principaux** de niveau  
  
-   Connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
-   Rôle de serveur  
  
 **Principaux au niveau des bases de données**  
  
-   Utilisateur de la base de données  
  
-   Rôle de base de données  
  
-   Rôle d'application  
  
## <a name="the-sql-server-sa-login"></a>La connexion SQL Server sa  
 La connexion sa [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est un principal au niveau du serveur. Par défaut, elle est créée lorsqu'une instance est installée. À compter de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], la base de données par défaut de sa est MASTER. Il s'agit là d'une différence par rapport aux versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="public-database-role"></a>Rôle de base de données public  
 Chaque utilisateur de base de données appartient au rôle de base de données public. Quand des autorisations spécifiques sur un élément sécurisable n’ont pas été accordées ni refusées à un utilisateur, celui-ci hérite des autorisations accordées à public sur cet élément sécurisable.  
  
## <a name="information_schema-and-sys"></a>INFORMATION_SCHEMA et sys  
 Chaque base de données inclut deux entités qui apparaissent comme des utilisateurs dans des affichages catalogue : INFORMATION_SCHEMA et sys. Ces entités sont requises par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ce ne sont pas des principaux et ils ne peuvent être ni modifiés, ni supprimés.  
  
## <a name="certificate-based-sql-server-logins"></a>Connexions SQL Server basées sur des certificats  
 Les principaux de serveur compris entre deux signes dièse (##) sont destinés uniquement à une utilisation système interne. Les principaux suivants sont créés à partir de certificats lors de l'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ; ils ne doivent pas être supprimés.  
  
-   \##MS_SQLResourceSigningCertificate##  
  
-   \##MS_SQLReplicationSigningCertificate##  
  
-   \##MS_SQLAuthenticatorCertificate##  
  
-   \##MS_AgentSigningCertificate##  
  
-   \##MS_PolicyEventProcessingLogin##  
  
-   \##MS_PolicySigningCertificate##  
  
-   \##MS_PolicyTsqlExecutionLogin##  
  
## <a name="the-guest-user"></a>Utilisateur invité  
 Chaque base de données inclut un **invité**. Les autorisations accordées à l'utilisateur **invité** sont héritées par les utilisateurs qui ont accès à la base de données, mais n'ont pas de compte d'utilisateur dans la base de données. L’utilisateur **invité** ne peut pas être supprimé, mais il peut être désactivé en révoquant son `CONNECT` autorisation. L' `CONNECT` autorisation peut être révoquée en exécutant `REVOKE CONNECT FROM GUEST` dans une base de données autre que Master ou tempdb.  
  
## <a name="client-and-database-server"></a>Client et serveur de base de données  
 Par définition, un client et un serveur de base de données sont des principaux de sécurité et peuvent être sécurisés. Ces entités peuvent être authentifiées mutuellement avant qu'une connexion réseau sécurisée soit établie. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]prend en charge le protocole d’authentification [Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758) , qui définit la manière dont les clients interagissent avec un service d’authentification réseau.  
  
## <a name="related-tasks"></a>Tâches associées  
 Les rubriques suivantes sont incluses dans cette section de la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   [Rubriques de procédures relatives à la gestion des connexions, des utilisateurs et des schémas](managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [Rôles de niveau serveur](server-level-roles.md)  
  
-   [Rôles au niveau de la base de données](database-level-roles.md)  
  
-   [Rôles d’application](application-roles.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation de SQL Server](../securing-sql-server.md)   
 [sys. database_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql)   
 [sys. server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)   
 [sys. sql_logins &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql)   
 [sys. database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)   
 [Rôles au niveau du serveur](server-level-roles.md)   
 [Rôles au niveau de la base de données](database-level-roles.md)  
  
  
