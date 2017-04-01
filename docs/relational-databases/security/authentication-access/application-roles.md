---
title: "R&#244;les d&#39;applications | Microsoft Docs"
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
  - "rôles d’application [SQL Server], à propos des rôles d’application"
  - "principaux [SQL Server], rôles d’application"
  - "informations d’identification [SQL Server], rôles"
  - "rôles d’application [SQL Server]"
  - "rôles d’application [SQL Server]"
  - "autorisations [SQL Server], rôles"
  - "utilisateurs [SQL Server], rôles d’application"
  - "authentification [SQL Server], rôles"
  - "groupes [SQL Server], rôles"
ms.assetid: dca18b8a-ca03-4b7f-9a46-8474d5b66f76
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# R&#244;les d&#39;applications
  Un rôle d'application est un principal de base de données qui permet à une application de s'exécuter avec ses propres autorisations de type utilisateur. Vous pouvez utiliser les rôles d'application pour permettre l'accès à des données spécifiques aux utilisateurs qui se connectent via une application spécifique. À la différence des rôles de base de données, les rôles d'application ne contiennent pas de membres et sont inactifs par défaut. Les rôles d'application fonctionnent avec les deux modes d'authentification. Les rôles d’application sont activés grâce à **sp_setapprole** qui nécessite un mot de passe. Les rôles d’application étant un principal au niveau des bases de données, ils peuvent uniquement accéder à d’autres bases de données par le biais des autorisations accordées dans ces bases de données à **invité**. Toute base de données où **invité** a été désactivé est donc inaccessible aux rôles d’application des autres bases de données.  
  
 Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les rôles d'application ne peuvent pas accéder à des métadonnées au niveau serveur, car ils ne sont pas associés à un principal au niveau serveur Pour désactiver cette restriction et permettre ainsi aux rôles d'application d'accéder aux métadonnées de niveau serveur, définissez l'indicateur global 4616. Pour plus d’informations, consultez [Indicateurs de trace &#40;Transact-SQL&#41;](../Topic/Trace%20Flags%20\(Transact-SQL\).md) et [DBCC TRACEON &#40;Transact-SQL&#41;](../../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md).  
  
## Connexion avec un rôle d'application  
 Les étapes suivantes composent le processus par lequel un rôle d'application fait basculer les contextes de sécurité :  
  
1.  Un utilisateur exécute une application cliente.  
  
2.  L'application cliente se connecte à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sous le nom de cet utilisateur.  
  
3.  L’application exécute ensuite la procédure stockée **sp_setapprole** avec un mot de passe uniquement connu pour l’application.  
  
4.  Si le nom et le mot de passe du rôle d'application sont valides, le rôle d'application est activé.  
  
5.  À ce stade, la connexion perd les autorisations de l'utilisateur et adopte les autorisations du rôle d'application.  
  
 Les autorisations acquises via le rôle d'application restent effectives pendant la durée de la connexion.  
  
 Dans les versions précédentes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], lorsqu'un utilisateur a démarré un rôle d'application, il peut récupérer son contexte de sécurité initial uniquement en se déconnectant de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et en s'y reconnectant. À partir de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **sp_setapprole** a une option qui crée un cookie. Le cookie contient des informations de contexte avant que le rôle d'application soit activé. Le cookie peut être utilisé par **sp_unsetapprole** pour rétablir la session à son contexte d’origine. Pour obtenir des informations sur cette nouvelle option et un exemple, consultez [sp_setapprole &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md).  
  
> [!IMPORTANT]  
>  L’option **encrypt** d’ODBC n’est pas prise en charge par **SqlClient**. Lorsque vous transmettez des informations confidentielles sur un réseau, utilisez le protocole SSL (Secure Sockets Layer) ou IPsec pour chiffrer le canal. Si vous devez conserver des informations d'identification dans l'application cliente, chiffrez-les à l'aide des fonctions API de chiffrement. Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et les versions ultérieures, le paramètre *password* est stocké sous la forme d’un hachage unidirectionnel.  
  
## Tâches associées  
  
|||  
|-|-|  
|Créer un rôle d'application.|[Créer un rôle d’application](../../../relational-databases/security/authentication-access/create-an-application-role.md) et [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/create-application-role-transact-sql.md)|  
|Modifier un rôle d'application.|[ALTER APPLICATION ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-application-role-transact-sql.md)|  
|Supprimer un rôle d'application.|[DROP APPLICATION ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-application-role-transact-sql.md)|  
|Utilisation d'un rôle d'application.|[sp_setapprole &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)|  
  
## Voir aussi  
 [Sécurisation de SQL Server](../../../relational-databases/security/securing-sql-server.md)  
  
  