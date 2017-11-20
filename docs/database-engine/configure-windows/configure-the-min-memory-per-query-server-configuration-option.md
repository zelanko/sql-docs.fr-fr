---
title: "Configurer l’option de configuration de serveur min memory per query | Microsoft Docs"
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
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e49ed68ce5e3f4621017db6cd09d2eec680b77f2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a>Configurer l'option de configuration de serveur min memory per query
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment configurer l'option de configuration de serveur **min memory per query** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L’option **min memory per query** spécifie la quantité minimale de mémoire (en kilo-octets) allouée pour l’exécution d’une requête. Par exemple, si la valeur attribuée à l'option **min memory per query** est 2048 Ko, la requête est assurée de bénéficier de cette quantité de mémoire, au minimum. La valeur par défaut est 1 024 Ko. La valeur minimale est de 512 Ko et la valeur maximale de 2 147 483 647 Ko (2 Go).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option min memory per query, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option min memory per query](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Le paramètre de l’option Mémoire minimum par requête prévaut par rapport à celui de l’option [index create memory](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md). Si vous modifiez ces deux options et que le paramètre index create memory est inférieur au paramètre min memory per query, un message d’avertissement s’affiche, mais la valeur définie est acceptée. Vous obtenez un avertissement similaire lors de l'exécution de requêtes.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Cette option avancée ne doit être modifiée que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Le processeur de requêtes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tente de déterminer la quantité de mémoire optimale à allouer à une requête. L'option min memory per query permet à l'administrateur de spécifier la quantité minimale de mémoire que reçoit n'importe quelle requête. Les requêtes reçoivent généralement une quantité de mémoire supérieure si elles doivent effectuer des opérations de hachage et de tri sur un volume de données important. L'attribution d'une valeur supérieure à min memory per query peut améliorer les performances pour certaines requêtes de taille petite à moyenne, mais cela risque de donner lieu à une concurrence accrue pour les ressources mémoire. L’option min memory per query inclut la mémoire allouée au tri.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>Pour configurer l'option min memory per query  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Mémoire** .  
  
3.  Dans la zone **Mémoire minimum par requête** , entrez la quantité minimale de mémoire (en kilo-octets) allouée pour l’exécution d’une requête.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>Pour configurer l'option min memory per query  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) pour attribuer à l’option `min memory per query` la valeur `3500` Ko.  
  
```tsql  
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
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option min memory per query  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Configurer l’option de configuration Création d’index en mémoire.](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md)  
  
  

