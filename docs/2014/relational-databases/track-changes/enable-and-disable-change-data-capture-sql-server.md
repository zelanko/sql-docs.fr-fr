---
title: Activer et désactiver la capture de données modifiées (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], enabling tables
- change data capture [SQL Server], enabling databases
- change data capture [SQL Server], disabling databases
- change data capture [SQL Server], disabling tables
ms.assetid: b741894f-d267-4b10-adfe-cbc14aa6caeb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f66cb56380f0e027d08e53154c05b7ad1e3be89f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62670575"
---
# <a name="enable-and-disable-change-data-capture-sql-server"></a>Activer et désactiver la capture de données modifiées (SQL Server)
  Cette rubrique décrit l'activation et la désactivation de la capture de données modifiées pour une base de données et une table.  
  
## <a name="enable-change-data-capture-for-a-database"></a>Activer la capture des données modifiées pour une base de données  
 Avant qu'une instance de capture puisse être créée pour des tables individuelles, un membre du rôle serveur fixe `sysadmin` doit d'abord activer la base de données pour la capture des données modifiées. Cela se fait en exécutant la procédure stockée [sys.sp_cdc_enable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql) dans le contexte de la base de données. Pour déterminer si une base de données est déjà activée, interrogez la colonne `is_cdc_enabled` dans l'affichage catalogue `sys.databases`.  
  
 Lorsqu'une base de données est activée pour la capture des données modifiées, le schéma `cdc`, l'utilisateur `cdc`, les tables de métadonnées, ainsi que d'autres objets systèmes sont créés pour la base de données. Le schéma `cdc` contient les tables de métadonnées de capture des données modifiées et, une fois que les tables sources sont activées pour la capture des données modifiées, les tables de modifications individuelles servent de base de données de référentiel pour les données modifiées. Le schéma `cdc` contient également les fonctions système associées utilisées pour rechercher les données modifiées.  
  
 La capture des données modifiées requiert une utilisation exclusive du schéma `cdc` et de l'utilisateur `cdc`. Si un schéma ou un utilisateur de base de données nommé *cdc* existe actuellement dans une base de données, celle-ci ne peut pas être activée pour la capture des données modifiées tant que le schéma et/ou l'utilisateur n'a pas été supprimé ou renommé.  
  
 Pour un exemple d'activation de base de données, consultez le modèle Activer la base de données pour la capture de données modifiées.  
  
> [!IMPORTANT]  
>  Pour repérer les modèles dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], allez dans **Afficher**, cliquez sur **Explorateur de modèles**, puis sélectionnez **Modèles SQL Server**. **Capture de données modifiées** est un sous-dossier. Sous ce dossier, vous trouverez tous les modèles auxquels il est fait référence dans cette rubrique. On trouve également une icône **Explorateur de modèles** dans la barre d'outils [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
```sql  
-- ====  
-- Enable Database for CDC template   
-- ====  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_db  
GO  
```  
  
## <a name="disable-change-data-capture-for-a-database"></a>Désactiver la capture des données modifiées pour une base de données  
 Un membre du rôle `sysadmin` serveur fixe peut exécuter la procédure stockée [sys. sp_cdc_disable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) dans le contexte de la base de données pour désactiver la capture de données modifiées pour une base de données. Il n'est pas nécessaire de désactiver individuellement les tables avant de désactiver la base de données. La désactivation de la base de données supprime toutes les métadonnées de capture de données modifiées associées, y compris l'utilisateur et le schéma `cdc`, ainsi que les travaux de capture de données modifiées. Toutefois, tous les rôles de régulation créés par capture de données modifiées ne seront pas supprimés automatiquement et doivent être supprimés explicitement. Pour déterminer si une base de données est activée, interrogez la colonne `is_cdc_enabled` dans l'affichage catalogue sys.databases.  
  
 Si une base de données sur laquelle la capture de données modifiées est activée est supprimée, les travaux de capture de données modifiées sont également et automatiquement supprimés.  
  
 Pour un exemple de désactivation d'une base de données, consultez le modèle Désactiver la base de données pour la capture de données modifiées.  
  
> [!IMPORTANT]  
>  Pour repérer les modèles dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], allez dans **Afficher**, cliquez sur **Explorateur de modèles**, puis sur **Modèles SQL Server**. **Capture de données modifiées** est un sous-dossier où vous trouverez tous les modèles qui sont référencés dans cette rubrique. On trouve également une icône **Explorateur de modèles** dans la barre d'outils [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
```sql  
-- =======  
-- Disable Database for Change Data Capture template   
-- =======  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_db  
GO  
```  
  
## <a name="enable-change-data-capture-for-a-table"></a>Activer la capture des données modifiées pour une table  
 Une fois qu'une base de données a été activée pour la capture des données modifiées, les membres du rôle de base de données fixe `db_owner` peuvent créer une instance de capture pour les tables sources individuelles à l'aide de la procédure stockée `sys.sp_cdc_enable_table`. Pour déterminer si une table source a été déjà activée pour la capture des données modifiées, examinez la colonne is_tracked_by_cdc dans l'affichage catalogue `sys.tables`.  
  
 Les options suivantes peuvent être spécifiées lorsque vous créez une instance de capture :  
  
 `Columns in the source table to be captured`.  
  
 Par défaut, toutes les colonnes de la table source sont identifiées comme colonnes capturées. Si seul un sous-ensemble de colonnes doit être suivi, par exemple pour des raisons de confidentialité ou de performance *@captured_column_list* , utilisez le paramètre pour spécifier le sous-ensemble de colonnes.  
  
 `A filegroup to contain the change table.`  
  
 Par défaut, la table de modifications se situe dans le groupe de fichiers par défaut de la base de données. Les propriétaires de bases de données qui souhaitent contrôler le placement des tables de modifications *@filegroup_name* individuelles peuvent utiliser le paramètre pour spécifier un groupe de fichiers particulier pour la table de modifications associée à l’instance de capture. Le groupe de fichiers nommé doit déjà exister. En règle générale, il est recommandé de placer des tables de modifications dans un groupe de fichiers séparé des tables sources. Consultez le `Enable a Table Specifying Filegroup Option` modèle pour obtenir un exemple qui illustre l' *@filegroup_name* utilisation du paramètre.  
  
```sql  
-- =========  
-- Enable a Table Specifying Filegroup Option Template  
-- =========  
USE MyDB  
GO  
  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@filegroup_name = N'MyDB_CT',  
@supports_net_changes = 1  
GO  
```  
  
 `A role for controlling access to a change table.`  
  
 L'objectif du rôle nommé consiste à contrôler l'accès aux données modifiées. Le rôle spécifié peut être un rôle serveur fixe existant ou un rôle de base de données. Si le rôle spécifié n'existe pas déjà, un rôle de base de données portant ce nom est automatiquement créé. Les membres du rôle `sysadmin` ou `db_owner` disposent d'un accès complet aux données des tables de modification. Tous les autres utilisateurs doivent disposer de l'autorisation SELECT pour toutes les colonnes capturées de la table source. De plus, lorsqu'un rôle est spécifié, les utilisateurs qui ne sont pas membres du rôle `sysadmin` or `db_owner` doivent également être membres du rôle spécifié.  
  
 Si vous ne souhaitez pas utiliser un rôle de régulation, affectez explicitement *@role_name* la valeur null au paramètre. Consultez le modèle `Enable a Table Without Using a Gating Role` pour obtenir un exemple de l'activation d'une table sans un rôle de régulation.  
  
```sql  
-- =========  
-- Enable a Table Without Using a Gating Role template   
-- =========  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = NULL,  
@supports_net_changes = 1  
GO  
  
```  
  
 `A function to query for net changes.`  
  
 Une instance de capture inclura toujours une fonction table pour retourner toutes les entrées de table de modifications qui ont eu lieu au cours d'un intervalle défini. On nomme cette fonction en ajoutant le nom de l'instance de capture à "cdc.fn_cdc_get_all_changes_". Pour plus d’informations, consultez [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql).  
  
 Si le paramètre *@supports_net_changes* a la valeur 1, une fonction de modifications nettes est également générée pour l’instance de capture. Cette fonction retourne une seule modification pour chaque ligne distincte modifiée dans l'intervalle spécifié dans l'appel. Pour plus d’informations, consultez [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).  
  
 Pour prendre en charge les requêtes de modifications nettes, la table source doit disposer d'une clé primaire ou d'un index unique permettant d'identifier sans ambiguïté les lignes. Si un index unique est utilisé, le nom de l’index doit être spécifié à l' *@index_name* aide du paramètre. Les colonnes définies dans la clé primaire ou l'index unique doivent être incluses dans la liste des colonnes sources à capturer.  
  
 Consultez le modèle `Enable a Table for All and Net Changes Queries` pour obtenir un exemple démontrant la création d'une instance de capture avec les deux fonctions de requête.  
  
```sql  
-- =============  
-- Enable a Table for All and Net Changes Queries template   
-- =============  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@supports_net_changes = 1  
GO  
```  
  
> [!NOTE]
>  Si la capture de données modifiées est activée sur une table avec une clé primaire existante et *@index_name* que le paramètre n’est pas utilisé pour identifier un autre index unique, la fonctionnalité de capture de données modifiées utilisera la clé primaire. Les modifications ultérieures à la clé primaire ne seront pas autorisées sans désactivation préalable de la capture de données modifiées pour la table. Cela est vrai, que la prise en charge des requêtes de modifications nettes ait été demandée ou non lors de la configuration de la capture de données. Si une table ne contient pas de clé primaire au moment de son activation pour la capture de données modifiées, tout ajout ultérieur de clé primaire sera ignoré par la capture des données modifiées. Étant donné que la capture de données modifiées n'utilisera pas de clé primaire créée une fois la table activée, la clé et les colonnes clés peuvent être supprimées sans restrictions.  
  
## <a name="disable-change-data-capture-for-a-table"></a>Désactiver la capture des données modifiées pour une table  
 Les membres du rôle de base de données fixe `db_owner` peuvent supprimer une instance de capture pour les tables sources individuelles à l'aide de la procédure stockée `sys.sp_cdc_disable_table`. Pour déterminer si une table source est actuellement activée pour la capture des données modifiées, examinez la colonne `is_tracked_by_cdc` dans l'affichage catalogue `sys.tables`. S'il n'y a pas de tables activées pour la base de données après la désactivation, les travaux de capture de données modifiées sont également supprimés.  
  
 Si une table pour laquelle la capture de données modifiées est activée est supprimée, les métadonnées de capture de données modifiées associées à la table sont automatiquement supprimées.  
  
 Pour un exemple de désactivation de table, consultez le modèle Désactiver une instance de capture pour une table.  
  
```sql  
-- =====  
-- Disable a Capture Instance for a Table template   
-- =====  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@capture_instance = N'dbo_MyTable'  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Suivre les modifications de données &#40;SQL Server&#41;](track-data-changes-sql-server.md)   
 [À propos de la capture de données modifiées &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md)   
 [Utiliser des données modifiées &#40;SQL Server&#41;](work-with-change-data-sql-server.md)   
 [Administrer et surveiller la capture de données modifiées &#40;SQL Server&#41;](../track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  
