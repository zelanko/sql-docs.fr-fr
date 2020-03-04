---
title: Configurer l’option de configuration de serveur max degree of parallelism | Microsoft Docs
ms.custom: ''
ms.date: 02/12/2020
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parallel queries [SQL Server]
- processors [SQL Server], parallel queries
- number of processors for parallel queries
- max degree of parallelism option
- MaxDop
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 94f8c87e0b996be0b9485cbe5a43038e33420fe0
ms.sourcegitcommit: d876425e5c465ee659dd54e7359cda0d993cbe86
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77568125"
---
# <a name="configure-the-max-degree-of-parallelism-server-configuration-option"></a>Configurer l'option de configuration de serveur max degree of parallelism
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment configurer l’option de configuration de serveur **max degree of parallelism (MAXDOP)** dans SQL Server à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Lorsqu'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute sur un ordinateur doté de plusieurs microprocesseurs ou UC, elle détecte le degré de parallélisme, qui correspond au nombre de processeurs employés pour exécuter une seule instruction, pour chaque exécution d'un plan parallèle. Vous pouvez utiliser l'option **max degree of parallelism** pour limiter le nombre de processeurs à utiliser lors de l'exécution des plans parallèles. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en compte les plans d’exécution parallèle pour les requêtes, les opérations du langage de définition de données (DDL) d’index, les insertions parallèles, la modification de colonne en ligne, la collecte de statistiques parallèle et l’alimentation des curseurs statiques et de jeux de clés.

> [!NOTE]
> [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] offre désormais des recommandations automatiques pour la définition de l’option de configuration du serveur MAXDOP lors du processus d’installation. L’interface utilisateur du programme d’installation vous permet d’accepter les paramètres recommandés ou d’entrer vos propres valeurs. Pour plus d’informations, consultez la [page Configuration du moteur de base de données - MaxDOP](../../sql-server/install/instance-configuration.md#maxdop).

##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si l'option affinity mask n'est pas définie sur la valeur par défaut, il est possible qu'elle limite le nombre de processeurs disponibles pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur les systèmes de multitraitement symétrique (SMP, symmetric multiprocessing).  

-   La limite du **degré maximal de parallélisme (MAXDOP)**  est spécifiée par [tâche](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md). Il ne s’agit pas d’une limite par [requête](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md). Cela signifie que lors d’une exécution de requête parallèle, une requête unique peut générer plusieurs tâches qui sont affectées à un planificateur. Pour plus d’informations, consultez le [Guide de l’architecture des threads et des tâches](../../relational-databases/thread-and-task-architecture-guide.md). 
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Seul un administrateur de base de données qualifié ou un spécialiste agréé doit changer cette option avancée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pour permettre au serveur de déterminer le degré maximal de parallélisme, définissez cette option sur 0, c'est-à-dire la valeur par défaut. Attribuer la valeur 0 à l'option Degré maximal de parallélisme permet à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'utiliser tous les processeurs disponibles, dans la limite de 64. Pour supprimer la génération de plans parallèles, attribuez **la valeur** 1 à l'option. Affectez la valeur à un nombre compris entre 1 et 32 767 pour spécifier le nombre maximal de noyaux de processeurs qui peuvent être utilisés par une seule exécution. Si une valeur supérieure au nombre de processeurs disponibles est spécifiée, le nombre réel de processeurs disponibles est utilisé. Si votre ordinateur est équipé d'un seul processeur, la valeur de l'option **max degree of parallelism** est ignorée.  
  
-   Vous pouvez remplacer la valeur de l'option max degree of parallelism dans les requêtes en spécifiant l'indicateur de requête MAXDOP dans l'instruction de requête. Pour plus d’informations, consultez [Indicateurs de requête &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md).  
  
-   Les opérations d'index destinées à créer ou à recréer un index, voire à supprimer un index cluster, peuvent nécessiter une quantité importante de ressources. Vous pouvez remplacer la valeur de l'option max degree of parallelism pour les opérations d'index en spécifiant l'option d'index MAXDOP dans l'instruction d'index. La valeur de MAXDOP est appliquée à l'instruction au moment de son exécution et n'est pas stockée dans les métadonnées de l'index. Pour plus d’informations, consultez [Configurer des opérations d’index parallèles](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
-   En plus des requêtes et des opérations d'index, cette option gère également le parallélisme de DBCC CHECKTABLE, DBCC CHECKDB et DBCC CHECKFILEGROUP. Vous pouvez désactiver les plans d'exécution parallèle pour ces instructions en utilisant l'indicateur de trace 2528. Pour plus d’informations, consultez [Indicateurs de trace &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).

> [!TIP]
> Pour définir cette option au niveau de la requête, utilisez l’[indicateur de requête](../../t-sql/queries/hints-transact-sql-query.md) **MAXDOP**.     
> Pour le faire au niveau de la base de données, utilisez la [configuration étendue à la base de données](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) **MAXDOP**.      
> Pour ce faire au niveau de la charge de travail, utilisez l’[option de configuration de groupe de charge de travail Resource Governor](../../t-sql/statements/create-workload-group-transact-sql.md) **MAX_DOP**.      

###  <a name="Guidelines"></a> Instructions  
Avec [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], lors du démarrage du service, si [!INCLUDE[ssde_md](../../includes/ssde_md.md)] détecte plus de huit cœurs physiques par socket ou nœud NUMA au démarrage, des nœuds soft-NUMA sont créés automatiquement par défaut. [!INCLUDE[ssde_md](../../includes/ssde_md.md)] place les processeurs logiques du même cœur physique dans différents nœuds soft-NUMA. Les recommandations contenues dans le tableau ci-dessous ont pour but de conserver tous les threads de travail d’une requête parallèle au sein du même nœud soft-NUMA. Cela améliorera les performances des requêtes et la distribution des threads de travail entre les nœuds NUMA pour la charge de travail. Pour plus d’informations, consultez [Soft-NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md).

Depuis [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], suivez les directives suivantes quand vous configurez la valeur de configuration de serveur **max degree of parallelism** :

||||
|----------------|-----------------|-----------------|
|Serveur avec un seul nœud NUMA|Inférieur ou égal à 8 processeurs logiques|Conserver MAXDOP à une valeur égale ou inférieure au nombre de processeurs logiques|
|Serveur avec un seul nœud NUMA|Supérieur à 8 processeurs logiques|Conservez MAXDOP à 8|
|Serveur avec plusieurs nœuds NUMA|Inférieur ou égal à 16 processeurs logiques par nœud NUMA|Conservez MAXDOP à une valeur égale ou inférieure au nombre de processeurs logiques par nœud NUMA|
|Serveur avec plusieurs nœuds NUMA|Plus de 16 processeurs logiques par nœud NUMA|Conservez MAXDOP à la moitié du nombre de processeurs logiques par nœud NUMA avec une valeur MAX de 16|
  
> [!NOTE]
> Le nœud NUMA dans la table ci-dessus fait référence à des nœuds soft-NUMA automatiquement créés par [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et versions ultérieures ou des nœuds NUMA si soft-NUMA a été désactivé .   
>  Utilisez ces instructions lorsque vous définissez l’option max degree of parallelism pour les groupes de charge de travail du Resource Governor. Pour plus d’informations, consultez [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md).
  
De [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] à [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], utilisez les directives suivantes quand vous configurez la valeur de configuration de serveur **max degree of parallelism** :

||||
|----------------|-----------------|-----------------|
|Serveur avec un seul nœud NUMA|Inférieur ou égal à 8 processeurs logiques|Conserver MAXDOP à une valeur égale ou inférieure au nombre de processeurs logiques|
|Serveur avec un seul nœud NUMA|Supérieur à 8 processeurs logiques|Conservez MAXDOP à 8|
|Serveur avec plusieurs nœuds NUMA|Inférieur ou égal à 8 processeurs logiques par nœud NUMA|Conservez MAXDOP à une valeur égale ou inférieure au nombre de processeurs logiques par nœud NUMA|
|Serveur avec plusieurs nœuds NUMA|Supérieur à 8 processeurs logiques par nœud NUMA|Conservez MAXDOP à 8|
  
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
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) pour attribuer à l’option `max degree of parallelism` la valeur `16`.  
  
```sql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 16;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l’option max degree of parallelism  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)      
 [Recommandations et directives pour l’option de configuration Degré maximal de parallélisme dans SQL Server](https://support.microsoft.com/help/2806535)     
 [affinity mask (option de configuration de serveur)](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Guide d’architecture de traitement des requêtes](../../relational-databases/query-processing-architecture-guide.md#DOP)       
 [Guide d’architecture de thread et de tâche](../../relational-databases/thread-and-task-architecture-guide.md)    
 [Configurer des opérations d'index parallèles](../../relational-databases/indexes/configure-parallel-index-operations.md)    
 [Indicateurs de requête &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)     
 [Définir les options d’index](../../relational-databases/indexes/set-index-options.md)     
