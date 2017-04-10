---
title: "Force du mot de passe de connexion SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "meilleures pratiques [moteur de base de données]"
ms.assetid: b0862c3a-926b-490c-a37f-382e50146a3e
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Force du mot de passe de connexion SQL Server
  Cette règle vérifie si l'option Conserver la stratégie de mot de passe est activée pour chaque connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est activée et si la version du système d'exploitation est antérieure à [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], un pirate peut régulièrement exploiter un mot de passe de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connu.  
  
## Meilleures pratiques recommandées  
 Nous vous recommandons de mettre à niveau le système d'exploitation vers [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].  
  
 Si l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas requise dans votre environnement, utilisez l'authentification Windows.  
  
 Activez l'option Conserver la stratégie de mot de passe pour toutes les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Utilisez [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) pour configurer la stratégie de mot de passe pour la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Pour plus d'informations  
 [Stratégie de mot de passe](../../relational-databases/security/password-policy.md)  
  
## Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  