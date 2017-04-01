---
title: "Informations d&#39;identification (moteur de base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "principaux [SQL Server], informations d’identification"
  - "schémas [SQL Server], informations d’identification"
  - "autorisations [SQL Server], informations d’identification"
  - "groupes [SQL Server], informations d’identification"
  - "ALTER ANY CREDENTIAL (autorisation)"
  - "sécurité [SQL Server], informations d’identification"
  - "authentification [SQL Server], informations d’identification"
  - "utilisateurs [SQL Server], informations d’identification"
  - "informations d’identification [SQL Server], à propos des informations d’identification"
  - "informations d'identification [SQL Server]"
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# Informations d&#39;identification (moteur de base de donn&#233;es)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../../includes/tsql-appliesto-ss2008-all-md.md)]

  Les informations d'identification correspondent à un enregistrement qui contient les informations d'authentification requises pour la connexion à une ressource en dehors de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ces informations sont utilisées en interne par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La plupart des informations d'identification contiennent un nom d'utilisateur et un mot de passe Windows.  
  
 Les informations stockées dans des informations d'identification permettent à un utilisateur connecté à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] par le biais de l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] d'accéder à des ressources en dehors de l'instance du serveur. Lorsque la source externe est Windows, l'utilisateur est authentifié en tant qu'utilisateur Windows, tel que spécifié dans les informations d'identification. Un groupe d'informations d'identification peut être mappé à plusieurs connexions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . En revanche, une connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut être mappée à un seul groupe d'informations d'identification.  
  
 Pour les informations d’identification qui sont stockées dans la base de données MASTER et qui peuvent être utilisées dans l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md). Pour les informations d’identification qui sont utilisées par une base de données spécifique et qui sont portables avec cette même base de données, consultez [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-database-scoped-credential-transact-sql.md).  
  
 Les informations d'identification système sont créées automatiquement et sont associées à des points de terminaison spécifiques. Le nom de ces informations d'identification système commence par deux signes dièse (##).  
  
 Pour plus d’informations sur les informations d’identification, consultez les affichages catalogue [sys.credentials](../../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md) et [sys.database_credentials &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-credentials-transact-sql.md).  
  
## Contenu connexe  
 [Créer des informations d’identification](../../../relational-databases/security/authentication-access/create-a-credential.md) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md) [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
  
 [Sécurisation de SQL Server](../../../relational-databases/security/securing-sql-server.md)  
  
  