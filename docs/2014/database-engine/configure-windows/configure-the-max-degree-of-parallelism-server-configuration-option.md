---
title: Configurer l’option de configuration de serveur max degree of parallelism | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parallel queries [SQL Server]
- processors [SQL Server], parallel queries
- number of processors for parallel queries
- max degree of parallelism option
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 46598cf66c80d07383fb033436bbe1792b1eec64
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537265"
---
# <a name="configure-the-max-degree-of-parallelism-server-configuration-option"></a>Configurer l'option de configuration de serveur max degree of parallelism
  Cette rubrique explique comment configurer le `max degree of parallelism` option de configuration de serveur dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)]. Lorsqu'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute sur un ordinateur doté de plusieurs microprocesseurs ou UC, elle détecte le degré de parallélisme optimal, qui correspond au nombre de processeurs employés pour exécuter une seule instruction, pour chaque exécution d'un plan parallèle. Vous pouvez utiliser l'option `max degree of parallelism` pour limiter le nombre de processeurs à utiliser dans une exécution de plans parallèles. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en compte les plans d’exécution parallèle pour l’alimentation des curseurs statiques et pilotés par les requêtes et opérations index data definition language (DDL).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer le max degree of parallelism option, à l’aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l’option max degree of parallelism](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si l'option affinity mask n'est pas définie sur la valeur par défaut, il est possible qu'elle limite le nombre de processeurs disponibles pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur les systèmes de multitraitement symétrique (SMP, symmetric multiprocessing).  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Cette option avancée ne doit être modifiée que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Pour permettre au serveur de déterminer le degré maximal de parallélisme, définissez cette option sur 0, c'est-à-dire la valeur par défaut. Attribuer la valeur 0 à l'option Degré maximal de parallélisme permet à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'utiliser tous les processeurs disponibles, dans la limite de 64. Pour supprimer la génération de plans parallèles, attribuez la valeur 1 à l'option `max degree of parallelism`. Affectez la valeur à un nombre compris entre 1 et 32 767 pour spécifier le nombre maximal de noyaux de processeurs qui peuvent être utilisés par une seule exécution. Si une valeur supérieure au nombre de processeurs disponibles est spécifiée, le nombre réel de processeurs disponibles est utilisé. Si l'ordinateur est équipé d'un seul processeur, la valeur de l'option `max degree of parallelism` est ignorée.  
  
-   Vous pouvez remplacer la valeur de l'option max degree of parallelism dans les requêtes en spécifiant l'indicateur de requête MAXDOP dans l'instruction de requête. Pour plus d’informations, consultez [Indicateurs de requête &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).  
  
-   Les opérations d'index destinées à créer ou à recréer un index, voire à supprimer un index cluster, peuvent nécessiter une quantité importante de ressources. Vous pouvez remplacer la valeur de l'option max degree of parallelism pour les opérations d'index en spécifiant l'option d'index MAXDOP dans l'instruction d'index. La valeur de MAXDOP est appliquée à l'instruction au moment de son exécution et n'est pas stockée dans les métadonnées de l'index. Pour plus d’informations, consultez [Configurer des opérations d’index parallèles](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
-   En plus des requêtes et des opérations d'index, cette option gère également le parallélisme de DBCC CHECKTABLE, DBCC CHECKDB et DBCC CHECKFILEGROUP. Vous pouvez désactiver les plans d'exécution parallèle pour ces instructions en utilisant l'indicateur de trace 2528. Pour plus d’informations, consultez [Indicateurs de trace &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>Pour configurer l'option max degree of parallelism  
  
1.  Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Avancé** .  
  
3.  Dans la zone **Degré maximal de parallélisme** , sélectionnez le nombre maximal de processeurs à utiliser au cours de l'exécution d'un plan parallèle.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>Pour configurer l'option max degree of parallelism  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) pour attribuer à l’option `max degree of parallelism` la valeur `8`.  
  
```sql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 8;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l’option max degree of parallelism  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [affinity mask (option de configuration de serveur)](affinity-mask-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)   
 [DBCC CHECKTABLE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql)   
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)   
 [DBCC CHECKFILEGROUP &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql)   
 [Configurer des opérations d'index parallèles](../../relational-databases/indexes/configure-parallel-index-operations.md)   
 [Indicateurs de requête &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)   
 [Définir les options d’index](../../relational-databases/indexes/set-index-options.md)  
  
  
