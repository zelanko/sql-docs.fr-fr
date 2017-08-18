---
title: "Configurer l’option de configuration de serveur index create memory | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- index create memory option
ms.assetid: 3d722d9b-bada-4bf5-a9d7-bfc556bb4915
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6140e8ea97b1854f18af5a3e9306b4bbe748efba
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="configure-the-index-create-memory-server-configuration-option"></a>Configurer l'option de configuration de serveur index create memory
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment configurer l'option de configuration de serveur **index create memory** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'option **index create memory** contrôle la quantité maximale de mémoire initialement allouée pour la création d'index. La valeur par défaut de cette option est 0 (auto-configuration). Si une quantité supplémentaire de mémoire est requise ultérieurement pour créer les index et que cette quantité de mémoire est disponible, le serveur l'utilisera, outrepassant ainsi le paramétrage de cette option. Si la mémoire supplémentaire requise n'est pas disponible, la création d'index se poursuivra en utilisant la mémoire déjà allouée.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option index create memory, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option index create memory](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Le paramétrage de l'option **min memory per query** prévaut par rapport à celui de l'option **index create memory** . Si vous modifiez ces deux options et que l’option **index create memory** est inférieur au paramètre **min memory per query**, un message d'avertissement s'affiche, mais la valeur définie est acceptée. Au cours de l'exécution d'une requête, un message d'avertissement similaire s'affiche.  
  
-   Lorsque vous utilisez des tables et des index partitionnés, la quantité minimale de mémoire requise pour la création d'index peut croître significativement en présence d'index partitionnés non alignés et d'un haut niveau de parallélisme. Cette option contrôle la quantité totale initiale de mémoire allouée pour toutes les partitions d'index, au sein d'une opération de création d'index. La requête se terminera par l'apparition d'un message d'erreur si la quantité définie par cette option est inférieure au minimum requis pour exécuter cette requête.  
  
-   La valeur d'exécution de cette option n'excédera pas la quantité réelle de mémoire pouvant être utilisée par le système d'exploitation et la plateforme matérielle sur lesquels [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Cette option avancée ne doit être modifiée que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   L’option **index create memory** est configurée automatiquement et fonctionne habituellement sans besoin de modification. Cependant, si vous rencontrez des difficultés dans la création d'index, envisagez d'augmenter la valeur de cette option par rapport à sa valeur d'exécution.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-index-create-memory-option"></a>Pour configurer l'option index create memory  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Mémoire** .  
  
3.  Sous **Mémoire de création de l'index**, tapez ou sélectionnez la valeur que vous souhaitez attribuer à l'option index create memory.  
  
     L'option **index create memory** permet de contrôler la quantité de mémoire utilisée par les tris de création d'index. L’option **index create memory** est configurée automatiquement et doit fonctionner dans la plupart des cas sans besoin de modification. Cependant, si vous rencontrez des difficultés dans la création d'index, envisagez d'augmenter la valeur de cette option par rapport à sa valeur d'exécution. Les tris de requête sont contrôlés au moyen de l'option **min memory per query** .  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-index-create-memory-option"></a>Pour configurer l'option index create memory  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) pour attribuer à l’option `index create memory` la valeur `4096`.  
  
```tsql  
USE AdventureWorks2012 ;  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
EXEC sp_configure 'index create memory', 4096  
GO  
RECONFIGURE;  
GO  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option index create memory  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [server memory (options de configuration du serveur)](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  

