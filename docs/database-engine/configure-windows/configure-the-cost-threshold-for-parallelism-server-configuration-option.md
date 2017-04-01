---
title: "Configure the cost threshold for parallelism Server Configuration Option | Microsoft Docs"
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
  - "cost threshold for parallelism (option)"
ms.assetid: dad21bee-fe28-41f6-9d2f-e6ababfaf9db
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Configure the cost threshold for parallelism Server Configuration Option
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment configurer l'option de configuration de serveur **Seuil de coût pour le parallélisme** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'option **Seuil de coût pour le parallélisme** spécifie le seuil de création et d'exécution des plans parallèles par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée et exécute un plan parallèle pour une requête uniquement lorsque le coût estimé de l'exécution d'un plan en série pour la même requête est supérieur à la valeur définie dans **Seuil de coût pour le parallélisme**. Ce coût est une estimation pour l’exécution du plan de série sur une configuration matérielle spécifique. Ce n’est pas une unité de temps. L'option de seuil de coût pour le parallélisme **cost threshold for parallelism** peut prendre toute valeur comprise entre 0 et 32 767. La valeur par défaut est 5.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option Seuil de coût pour le parallélisme, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option Seuil de coût pour le parallélisme](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Ce coût est une unité de coût abstraite et non une unité de temps estimé. Spécifiez **cost threshold for parallelism** uniquement sur des multiprocesseurs symétriques.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ignore la valeur de l'option de seuil de coût pour le parallélisme **cost threshold for parallelism** dans les conditions suivantes :  
  
    -   L'ordinateur ne dispose que d'un seul processeur logique.  
  
    -   Un seul processeur logique est disponible pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en raison de l’option de configuration **masque d’affinité**.  
  
    -   L'option de degré maximal de parallélisme **max degree of parallelism** a la valeur 1.  
  
 Un processeur logique correspond à l'unité de base d'un processeur qui permet au système d'exploitation de distribuer une tâche ou d'exécuter un contexte de thread. Chaque processeur logique peut exécuter uniquement un contexte de thread à la fois. Le noyau du processeur désigne le circuit qui permet de décoder et d'exécuter des instructions. Un noyau de processeur peut contenir un ou plusieurs processeurs logiques. La requête [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante peut être utilisée pour obtenir les informations de l'UC pour le système.  
  
```  
SELECT (cpu_count / hyperthread_ratio) AS PhysicalCPUs,   
cpu_count AS logicalCPUs   
FROM sys.dm_os_sys_info  
```  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Cette option avancée ne doit être modifiée que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Dans certains cas, un plan parallèle peut être choisi, même si le plan de coût de la requête est inférieur à la valeur actuelle de l'option **Seuil de coût pour le parallélisme** . Cela s'explique par le fait que la décision d'utilisation d'un plan parallèle ou d'un plan en série prend comme base une estimation de coût fournie avant que l'optimisation soit terminée.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure**, sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres pour modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour configurer l'option Seuil de coût pour le parallélisme  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Avancé** .  
  
3.  Sous **Parallélisme**, remplacez l'option **Seuil de coût pour le parallélisme** par la valeur souhaitée. Tapez ou sélectionnez une valeur comprise entre 0 et 32 767.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour configurer l'option Seuil de coût pour le parallélisme  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) pour attribuer à l’option `cost threshold for parallelism` la valeur `10`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cost threshold for parallelism', 10 ;  
GO  
RECONFIGURE  
GO  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option Seuil de coût pour le parallélisme  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## Voir aussi  
 [Configurer des opérations d'index parallèles](../../relational-databases/indexes/configure-parallel-index-operations.md)   
 [Indicateurs de requête &#40;Transact-SQL&#41;](../Topic/Query%20Hints%20\(Transact-SQL\).md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [Masque d'affinité (option de configuration de serveur)](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  