---
title: cross db ownership chaining (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cross-database ownership chaining
- cross db ownership chaining option
- chaining ownership
ms.assetid: 7b2d49f2-b91c-4aee-a52b-6cc49bed03af
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5630579e787a3bfcb5d64ee3bcf0ec5bee368611
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62782393"
---
# <a name="cross-db-ownership-chaining-server-configuration-option"></a>cross db ownership chaining (option de configuration de serveur)
  Utilisez l’option **cross db ownership chaining** pour configurer le chaînage des propriétés des bases de données croisées pour une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Cette option de serveur vous permet de contrôler le chaînage des propriétés des bases de données croisées au niveau de la base de données ou d'autoriser le chaînage des propriétés des bases de données croisées pour toutes les bases de données :  
  
-   Lorsque l’option **cross db ownership chaining** est désactivée (0) pour l’instance, le chaînage des propriétés des bases de données croisées est désactivé pour toutes les bases de données.  
  
-   Lorsque l’option **cross db ownership chaining** est activée (1) pour l’instance, le chaînage des propriétés des bases de données croisées est activé pour toutes les bases de données.  
  
-   Vous pouvez définir le chaînage des propriétés des bases de données croisées pour des bases de données spécifiques à l'aide de la clause SET de l'instruction ALTER DATABASE. Si vous créez une nouvelle base de données, vous pouvez définir l'option de chaînage des propriétés des bases de données croisées pour la nouvelle base de données à l'aide de l'instruction CREATE DATABASE.  
  
     Il n’est pas recommandé d’attribuer la valeur 1 à l’option **Chaînage des propriétés des bases de données croisées** , sauf si toutes les bases de données hébergées par l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent participer au chaînage des propriétés des bases de données croisées et que vous êtes conscient de l’impact de ce paramétrage sur la sécurité.  
  
## <a name="controlling-cross-database-ownership-chaining"></a>Contrôle du chaînage des propriétés des bases de données croisées  
 Avant d'activer ou de désactiver le chaînage des propriétés des bases de données croisées, prenez en considération les points suivants :  
  
-   Vous devez être membre du rôle serveur fixe **sysadmin** pour activer ou désactiver le chaînage des propriétés des bases de données croisées.  
  
-   Avant de désactiver le chaînage des propriétés des bases de données croisées sur un serveur de production, testez entièrement toutes les applications, y compris les applications de tierces parties, pour vérifier que les modifications n'affectent pas leurs fonctionnalités.  
  
-   Vous pouvez modifier l’option **cross db ownership chaining** pendant que le serveur est en cours d’exécution si vous spécifiez RECONFIGURE avec **sp_configure**.  
  
-   Si des bases de données spécifiques requièrent le chaînage des propriétés des bases de données croisées, il est conseillé de désactiver l’option **cross db ownership chaining** pour l’instance à l’aide de **sp_configure**; ensuite, activez le chaînage des propriétés des bases de données croisées pour les bases de données qui le requièrent à l’aide de l’instruction ALTER DATABASE.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
