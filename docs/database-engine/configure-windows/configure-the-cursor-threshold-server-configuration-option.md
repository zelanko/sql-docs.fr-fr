---
title: "Configurer l’option de configuration de serveur cursor threshold | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursor threshold option
ms.assetid: 189f2067-c6c4-48bd-9bd9-65f6b2021c12
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b17a4177e481059db1fa71b5e727590aca377b75
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="configure-the-cursor-threshold-server-configuration-option"></a>Configurer l'option de configuration de serveur cursor threshold
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment configurer l'option de configuration de serveur **cursor threshold** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Le **seuil du curseur** option spécifie le nombre de lignes du jeu de curseurs à partir desquelles les jeux de clés de curseurs sont générés de façon asynchrone. Lorsque le curseur génère un jeu de clés pour un jeu de résultats, l'optimiseur de requête évalue le nombre de lignes renvoyées pour ce jeu de résultats. Si l'optimiseur de requête estime que le nombre de lignes renvoyées est plus élevé que ce seuil, le curseur est généré de façon asynchrone, ce qui permet à l'utilisateur de rechercher des lignes à partir du curseur alors que ce dernier continue d'être rempli. Dans le cas contraire, le curseur est généré de façon synchrone et la requête attend que toutes les lignes soient renvoyées.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option cursor threshold, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option cursor threshold](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge la génération asynchrone de curseurs [!INCLUDE[tsql](../../includes/tsql-md.md)] pilotés par jeux de clés ou statiques. [!INCLUDE[tsql](../../includes/tsql-md.md)] sur les curseurs telles que OPEN ou FETCH sont exécutées par lot : la génération asynchrone de curseurs [!INCLUDE[tsql](../../includes/tsql-md.md)] n'est donc pas nécessaire. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] continue de prendre en charge les curseurs côté serveur d’API pilotés par jeux de clés ou statiques asynchrones si l’opération de curseur OPEN présente une latence trop faible, en raison des boucles clientes de chaque opération de curseur.  
  
-   La précision avec laquelle l'optimiseur de requête va évaluer le nombre de lignes d'un jeu de clés dépend du degré d'actualité des statistiques pour chacune des tables dans le curseur.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Cette option avancée ne doit être modifiée que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Si vous attribuez la valeur -1 à l’option **Seuil du curseur** , tous les jeux de clés sont générés de façon synchrone (ce qui avantage les jeux de curseurs de petite taille). Si vous attribuez la valeur 0 à l'option **cursor threshold** , tous les jeux de clés de curseurs sont générés de manière asynchrone. Si d'autres valeurs sont définies, l'optimiseur de requêtes compare le nombre estimé de lignes du jeu de curseurs et crée le jeu de clés de façon asynchrone si ce nombre dépasse celui de l'option **cursor threshold**. N'attribuez pas une valeur trop faible à l'option **Seuil du curseur** , sachant que les petits jeux de résultats sont mieux générés de manière synchrone.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-cursor-threshold-option"></a>Pour configurer l'option cursor threshold  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Avancé** .  
  
3.  Sous **Divers**, modifiez l'option **Seuil du curseur** selon vos besoins.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-cursor-threshold-option"></a>Pour configurer l'option cursor threshold  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) pour attribuer à l’option `cursor threshold` la valeur `0` pour que les jeux de clés du curseur soient générés de façon asynchrone.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cursor threshold', 0 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option cursor threshold  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [@@CURSOR_ROWS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-rows-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)  
  
  

