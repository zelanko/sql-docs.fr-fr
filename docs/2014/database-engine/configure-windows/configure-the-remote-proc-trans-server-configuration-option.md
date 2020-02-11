---
title: Configurer l’option de configuration de serveur remote proc trans | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote proc trans option
- distributed transactions [SQL Server], enforcing
ms.assetid: cfbc6158-ab96-44b4-87eb-ea278c1b0c6b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 106f4ca8951200110349809065b35ba65a7f8411
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62811333"
---
# <a name="configure-the-remote-proc-trans-server-configuration-option"></a>Configurer l'option de configuration de serveur remote proc trans
  Cette rubrique explique comment configurer l'option de configuration de serveur **remote proc trans** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L’option **remote proc trans** contribue à protéger les actions d’une procédure de serveur à serveur via une transaction MS DTC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator).  
  
 Attribuez la valeur 1 à l’option **remote proc trans** pour obtenir une transaction distribuée coordonnée par MS DTC qui protège les propriétés ACID (Atomicité, Cohérence, Isolation et Durabilité) des transactions. Les sessions qui commencent après l'attribution de la valeur 1 à cette option héritent par défaut des options de configuration.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Prérequis](#Prerequisites)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l’option REMOTE PROC TRANS, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [après avoir configuré l’option transactions de procédures distantes](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a>Conditions préalables  
  
-   Les connexions au serveur distant doivent être autorisées avant que cette valeur puisse être définie.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Cette option est fournie à des fins de compatibilité avec [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les versions antérieures de pour les applications qui utilisent des procédures stockées distantes. Au lieu d’émettre des appels de procédures stockées distantes, utilisez des requêtes distribuées faisant référence à des serveurs liés, qui sont définis à l’aide de [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a>Pour configurer l'option remote proc trans  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Connexions** .  
  
3.  Sous **Connexions au serveur distant**, activez la case à cocher **Nécessite des transactions distribuées pour la communication de serveur à serveur** .  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a>Pour configurer l'option remote proc trans  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) pour attribuer à l’option `remote proc trans` la valeur `1`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote proc trans', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a>Suivi : après avoir configuré l’option transactions de procédures distantes  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
