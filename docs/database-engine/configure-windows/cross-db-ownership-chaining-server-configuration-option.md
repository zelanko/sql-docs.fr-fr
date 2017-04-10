---
title: "Cha&#238;nage des propri&#233;t&#233;s des bases de donn&#233;es crois&#233;es (option de configuration de serveur) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "chaînage des propriétés des bases de données croisées"
  - "cross db ownership chaining (option)"
  - "chaînage des propriétés"
ms.assetid: 7b2d49f2-b91c-4aee-a52b-6cc49bed03af
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# Cha&#238;nage des propri&#233;t&#233;s des bases de donn&#233;es crois&#233;es (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option **Chaînage des propriétés des bases de données croisées** pour configurer le chaînage des propriétés des bases de données croisées pour une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Cette option de serveur vous permet de contrôler le chaînage des propriétés des bases de données croisées au niveau de la base de données ou d'autoriser le chaînage des propriétés des bases de données croisées pour toutes les bases de données :  
  
-   Lorsque l’option **Chaînage des propriétés des bases de données croisées** est désactivée (0) pour l’instance, le chaînage des propriétés des bases de données croisées est désactivé pour toutes les bases de données.  
  
-   Lorsque l’option **Chaînage des propriétés des bases de données croisées** est activée (1) pour l’instance, le chaînage des propriétés des bases de données croisées est activé pour toutes les bases de données.  
  
-   Vous pouvez définir le chaînage des propriétés des bases de données croisées pour des bases de données spécifiques à l'aide de la clause SET de l'instruction ALTER DATABASE. Si vous créez une nouvelle base de données, vous pouvez définir l'option de chaînage des propriétés des bases de données croisées pour la nouvelle base de données à l'aide de l'instruction CREATE DATABASE.  
  
     Il n’est pas recommandé d’attribuer la valeur 1 à l’option **Chaînage des propriétés des bases de données croisées**, sauf si toutes les bases de données hébergées par l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent participer au chaînage des propriétés des bases de données croisées et que vous êtes conscient de l’impact de ce paramétrage sur la sécurité.  
  
## Contrôle du chaînage des propriétés des bases de données croisées  
 Avant d'activer ou de désactiver le chaînage des propriétés des bases de données croisées, prenez en considération les points suivants :  
  
-   Vous devez être membre du rôle serveur fixe **sysadmin** pour activer ou désactiver le chaînage des propriétés des bases de données croisées.  
  
-   Avant de désactiver le chaînage des propriétés des bases de données croisées sur un serveur de production, testez entièrement toutes les applications, y compris les applications de tierces parties, pour vérifier que les modifications n'affectent pas leurs fonctionnalités.  
  
-   Vous pouvez modifier l’option **Chaînage des propriétés des bases de données croisées** pendant que le serveur est en cours d’exécution si vous spécifiez RECONFIGURE avec **sp_configure**.  
  
-   Si des bases de données spécifiques requièrent le chaînage des propriétés des bases de données croisées, il est conseillé de désactiver l’option **Chaînage des propriétés des bases de données croisées** pour l’instance à l’aide de **sp_configure** ; ensuite, activez le chaînage des propriétés des bases de données croisées pour les bases de données qui le requièrent à l’aide de l’instruction ALTER DATABASE.  
  
## Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  