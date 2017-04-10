---
title: "Afficher ou configurer l&#39;option de configuration du serveur valeur par d&#233;faut de compression de la sauvegarde | Microsoft Docs"
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
  - "SQL Server Management Studio [SQL Server], option par défaut de compression de la sauvegarde"
  - "compression de la sauvegarde [SQL Server], option par défaut de compression de la sauvegarde"
ms.assetid: 23029395-3e93-4c29-b7d6-e5a47a3526ff
caps.latest.revision: 30
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 30
---
# Afficher ou configurer l&#39;option de configuration du serveur valeur par d&#233;faut de compression de la sauvegarde
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment afficher ou configurer l’option de configuration du serveur **valeur par défaut de compression de la sauvegarde** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L’option **valeur par défaut de compression de la sauvegarde** détermine si l’instance de serveur crée des sauvegardes compressées par défaut. Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé, l’option **valeur par défaut de compression de la sauvegarde** est désactivée.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour afficher ou configurer l'option valeur par défaut de compression de la sauvegarde, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option valeur par défaut de compression de la sauvegarde](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   La compression de la sauvegarde n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
-   Par défaut, la compression augmente considérablement l'utilisation de l'UC et l'UC supplémentaire consommée par le processus de compression peut avoir un impact néfaste sur les opérations simultanées. Il peut donc être préférable, dans une session où l’utilisation de l’UC est limitée, de créer une sauvegarde compressée de priorité basse à l’aide de [Resource Governor](../../relational-databases/resource-governor/resource-governor.md). Pour plus d’informations, consultez [Utiliser Resource Governor pour limiter l’utilisation de l’UC par compression de la sauvegarde &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Lors de la création d'une sauvegarde individuelle, de la configuration de la copie des journaux de transaction ou de la création d'un plan de maintenance, vous pouvez remplacer la valeur par défaut au niveau du serveur.  
  
-   La compression de la sauvegarde est prise en charge pour les unités de sauvegarde sur disque et les périphériques de sauvegarde sur bande.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure**, sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres pour modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour afficher ou configurer l'option valeur par défaut de compression de la sauvegarde  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Paramètres de base de données** .  
  
3.  Sous **Sauvegarde et restauration**, **Compresser la sauvegarde** affiche le paramètre actuel de l’option **valeur par défaut de compression de la sauvegarde** . Ce paramètre détermine la valeur par défaut au niveau du serveur pour la compression des sauvegardes, comme suit :  
  
    -   Si la case à cocher **Compresser la sauvegarde** est désactivée, les nouvelles sauvegardes ne sont pas compressées par défaut.  
  
    -   Si la case à cocher **Compresser la sauvegarde** est activée, les nouvelles sauvegardes sont compressées par défaut.  
  
     Si vous êtes membre du rôle serveur fixe **sysadmin** ou **serveradmin** , vous pouvez également modifier le paramètre par défaut en activant la case à cocher **Compresser la sauvegarde** .  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour afficher l'option valeur par défaut de compression de la sauvegarde  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple suivant interroge la vue de catalogue [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) pour déterminer la valeur de `backup compression default`. La valeur 0 indique que la compression de la sauvegarde est désactivée, et la valeur 1 indique que la compression de la sauvegarde est activée.  
  
```tsql  
SELECT value   
FROM sys.configurations   
WHERE name = 'backup compression default' ;  
GO  
```  
  
#### Pour configurer l'option de compression de la sauvegarde par défaut  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) pour configurer l’instance de serveur afin de créer des sauvegardes compressées par défaut.  
  
```tsql  
EXEC sp_configure 'backup compression default', 1 ;  
RECONFIGURE WITH OVERRIDE ;  
GO 
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option de compression de la sauvegarde par défaut  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)  
  
  