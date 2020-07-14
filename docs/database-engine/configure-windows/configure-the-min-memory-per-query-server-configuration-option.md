---
title: Configurer l’option de configuration de serveur min memory per query | Microsoft Docs
description: Découvrez comment utiliser l’option Mémoire minimum par requête pour spécifier l’allocation de mémoire minimale, ou le nombre minimal de kilo-octets que SQL Server alloue pour une requête.
ms.custom: ''
ms.date: 11/24/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
- min memory grant
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 784dc57403cdb5c8dad6ba3e8f910ecd6d4dee26
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85696851"
---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a>Configurer l'option de configuration de serveur min memory per query
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Cette rubrique explique comment configurer l'option de configuration de serveur **min memory per query** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L’option **min memory per query** spécifie la quantité minimale de mémoire (en kilo-octets) allouée pour l’exécution d’une requête. Cela est également appelé « allocation de mémoire minimale ». Par exemple, si la valeur attribuée à l'option **min memory per query** est 2048 Ko, la requête est assurée de bénéficier de cette quantité de mémoire, au minimum. La valeur par défaut est 1 024 Ko. La valeur minimale est de 512 Ko et la valeur maximale de 2 147 483 647 Ko (2 Go).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option min memory per query, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l’option min memory per query](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   La valeur du paramètre min memory per query prévaut par rapport à celle du paramètre [index create memory](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md). Si vous modifiez ces deux options et que le paramètre index create memory est inférieur au paramètre min memory per query, un message d’avertissement s’affiche, mais la valeur définie est acceptée. Lors de l’exécution de requêtes, vous recevez un autre avertissement similaire.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
  
-   Seul un administrateur de base de données qualifié ou un spécialiste agréé doit changer cette option avancée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Le processeur de requêtes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tente de déterminer la quantité de mémoire optimale à allouer à une requête. L'option min memory per query permet à l'administrateur de spécifier la quantité minimale de mémoire que reçoit n'importe quelle requête. Les requêtes reçoivent généralement une quantité de mémoire supérieure si elles doivent effectuer des opérations de hachage et de tri sur un grand volume de données. L'attribution d'une valeur supérieure à min memory per query peut améliorer les performances pour certaines requêtes de taille petite à moyenne, mais cela risque de donner lieu à une concurrence accrue pour les ressources mémoire. L’option min memory per query inclut la mémoire allouée aux opérations de tri.  

-    N’affectez pas une valeur trop élevée à l’option de configuration du serveur min memory per query, en particulier sur des systèmes très sollicités, car la requête devra attendre <sup>1</sup> qu’elle puisse sécuriser la mémoire minimale demandée ou que la valeur spécifiée dans l’option de configuration du serveur d’attente de la requête soit atteinte. S'il y a plus de mémoire disponible pour exécuter la requête que ne le demande la valeur minimale spécifiée, la requête aura l'autorisation d'utiliser la mémoire additionnelle, à condition que cette mémoire puisse être utilisée efficacement par la requête.     

<sup>1</sup> Dans ce scénario, le type d’attente est généralement RESOURCE_SEMAPHORE. Pour plus d’informations, consultez [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).

###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>Pour configurer l'option min memory per query  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Mémoire** .  
  
3.  Dans la zone **Mémoire minimum par requête** , entrez la quantité minimale de mémoire (en kilo-octets) allouée pour l’exécution d’une requête.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>Pour configurer l'option min memory per query  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) pour attribuer à l’option `min memory per query` la valeur `3500` Ko.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'min memory per query', 3500 ;  
GO  
RECONFIGURE;  
GO    
```  
  
##  <a name="follow-up-after-you-configure-the-min-memory-per-query-option"></a><a name="FollowUp"></a> Suivi : Après avoir configuré l’option min memory per query  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Configurer l’option de configuration Création d’index en mémoire.](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md)     
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)     
 [sys.dm_exec_query_memory_grants &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)
  
  
