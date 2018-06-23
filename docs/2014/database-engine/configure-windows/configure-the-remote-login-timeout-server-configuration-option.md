---
title: Configurer l’option de configuration de serveur remote login timeout | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- remote login timeout option
ms.assetid: 077adebe-0e3f-42a5-a75e-5e6d04847e2b
caps.latest.revision: 26
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5fb4ac975ccccd4bfcc809c6871f9cb7f53596ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043219"
---
# <a name="configure-the-remote-login-timeout-server-configuration-option"></a>Configurer l'option de configuration de serveur remote login timeout
  Cette rubrique explique comment configurer l'option de configuration de serveur **remote login timeout** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'option **Délai d'attente de la connexion distante** spécifie le nombre de secondes d'attente avant le renvoi d'une tentative de connexion à un serveur distant qui a échoué. Par exemple, si vous tentez de vous connecter à un serveur distant et que ce serveur est arrêté, l'option **remote login timeout** vous assure de ne pas attendre indéfiniment que votre ordinateur cesse ses tentatives de connexion. La valeur par défaut de cette option est de 10 secondes. Une valeur égale à 0 entraîne une attente infinie.  
  
> [!NOTE]  
>  La valeur par défaut de cette option est de 20 secondes dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option remote login timeout, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option remote login timeout](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   L'option **remote login timeout** concerne les connexions à des fournisseurs OLE DB établies pour des requêtes hétérogènes.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a>Pour configurer l'option remote login timeout  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Avancé** .  
  
3.  Sous **Réseau**, sélectionnez une valeur pour la zone **Remote Login Timeout** .  
  
     Utilisez l'option **remote login timeout** pour spécifier le nombre de secondes d'attente avant le renvoi d'une tentative de connexion qui a échoué.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-remote-login-timeout-option"></a>Pour configurer l'option remote login timeout  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) pour attribuer à l’option `remote login timeout` la valeur `35` secondes.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote login timeout', 35 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option remote login timeout  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
