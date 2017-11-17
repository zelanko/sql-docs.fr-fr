---
title: "ALTER DATABASE (base de données SQL Azure) | Documents Microsoft"
ms.custom: 
ms.date: 09/25/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fc5fd95-2045-4f20-a914-3598091bc7cc
caps.latest.revision: 37
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: e3c781449a8f7a1b236508cd21b8c00ff175774f
ms.openlocfilehash: f525c0ca01f49be05c1920897951059b126c83e9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/30/2017

---
# <a name="alter-database-azure-sql-database"></a>ALTER DATABASE (base de données SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Modifie un [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Modifie le nom d’un objectif de la base de données, l’édition et le service d’une base de données, un pool élastique de jointure et définit les options de base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Azure SQL Database Syntax  
ALTER DATABASE { database_name }  
{  
    MODIFY NAME = new_database_name  
  | MODIFY ( <edition_options> [, ... n] )   
  | SET { <option_spec> [ ,... n ] }   
  | ADD SECONDARY ON SERVER <partner_server_name>  
      [WITH ( <add-secondary-option>::= [, ... n] ) ]  
  | REMOVE SECONDARY ON SERVER <partner_server_name>  
  | FAILOVER  
  | FORCE_FAILOVER_ALLOW_DATA_LOSS  
}  
[;] 

<edition_options> ::=   
{  

      MAXSIZE = { 100 MB | 250 MB | 500 MB | 1 … 1024 … 4096 GB }    
    | EDITION = { 'basic' | 'standard' | 'premium' | 'premiumrs' }   
    | SERVICE_OBJECTIVE = 
                 {  <service-objective>
                 | { ELASTIC_POOL (name = <elastic_pool_name>) }   
                 }   
}  

<add-secondary-option> ::=  
   {  
      ALLOW_CONNECTIONS = { ALL | NO }  
     | SERVICE_OBJECTIVE =   
                 {  <service-objective> 
                 | { ELASTIC_POOL ( name = <elastic_pool_name>) }   
                 }   
   }  

<service-objective> ::=  { 'S0' | 'S1' | 'S2' | 'S3'| 'S4'| 'S6'| 'S7'| 'S9'| 'S12' |
                 | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15' | 
                 | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' | }

```  
  
```
-- SET OPTIONS AVAILABLE FOR SQL Database  
-- Full descriptions of the set options are available in the topic   
-- ALTER DATABASE SET Options. The supported syntax is listed here.  

<optionspec> ::=   
{  
    <auto_option>   
  | <compatibility_level_option>  
  | <cursor_option>   
  | <db_encryption_option>  
  | <db_update_option>   
  | <db_user_access_option>   
  | <delayed_durability_option>  
  | <parameterization_option>  
  | <query_store_options>  
  | <snapshot_option>  
  | <sql_option>   
  | <target_recovery_time_option>   
  | <termination>  
  | <temporal_history_retention>  
}  
  
<auto_option> ::=   
{  
    AUTO_CREATE_STATISTICS { OFF | ON [ ( INCREMENTAL = { ON | OFF } ) ] }   
  | AUTO_SHRINK { ON | OFF }   
  | AUTO_UPDATE_STATISTICS { ON | OFF }   
  | AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }  
}  
  
<compatibility_level_option>::=  
COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }  
  
<cursor_option> ::=   
{  
    CURSOR_CLOSE_ON_COMMIT { ON | OFF }   
}  
  
<db_encryption_option> ::=  
    ENCRYPTION { ON | OFF }  
  
<db_update_option> ::=  
    { READ_ONLY | READ_WRITE }  
  
<db_user_access_option> ::=  
    { RESTRICTED_USER | MULTI_USER }  
  
<delayed_durability_option> ::=    DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
  
<parameterization_option> ::=  
    PARAMETERIZATION { SIMPLE | FORCED }  
  
<query_store_options> ::=  
{  
    QUERY_STORE   
    {  
          = OFF   
        | = ON [ ( <query_store_option_list> [,... n] ) ]  
        | ( < query_store_option_list> [,... n] )  
        | CLEAR [ ALL ]  
    }  
}   
  
<query_store_option_list> ::=  
{  
      OPERATION_MODE = { READ_WRITE | READ_ONLY }   
    | CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = number )  
    | DATA_FLUSH_INTERVAL_SECONDS = number   
    | MAX_STORAGE_SIZE_MB = number   
    | INTERVAL_LENGTH_MINUTES = number   
    | SIZE_BASED_CLEANUP_MODE = [ AUTO | OFF ]  
    | QUERY_CAPTURE_MODE = [ ALL | AUTO | NONE ]  
    | MAX_PLANS_PER_QUERY = number  
}  
  
<snapshot_option> ::=  
{  
    ALLOW_SNAPSHOT_ISOLATION { ON | OFF }  
  | READ_COMMITTED_SNAPSHOT {ON | OFF }  
  | MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT {ON | OFF }  
}  
<sql_option> ::=   
{  
    ANSI_NULL_DEFAULT { ON | OFF }   
  | ANSI_NULLS { ON | OFF }   
  | ANSI_PADDING { ON | OFF }   
  | ANSI_WARNINGS { ON | OFF }   
  | ARITHABORT { ON | OFF }   
  | COMPATIBILITY_LEVEL = { 90 | 100 | 110 | 120}  
  | CONCAT_NULL_YIELDS_NULL { ON | OFF }   
  | NUMERIC_ROUNDABORT { ON | OFF }   
  | QUOTED_IDENTIFIER { ON | OFF }   
  | RECURSIVE_TRIGGERS { ON | OFF }   
}  
  
<termination>  ::=   
{  
    ROLLBACK AFTER integer [ SECONDS ]   
  | ROLLBACK IMMEDIATE   
  | NO_WAIT  
}  

<temporal_history_retention>  ::=  TEMPORAL_HISTORY_RETENTION { ON | OFF }
```  
  
 Pour obtenir une description complète des options set, consultez [Options ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) et [modifier le niveau de compatibilité de base de données &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Nom de la base de données à modifier.  
  
 CURRENT  
 Indique que la base de données actuelle en cours d'utilisation doit être modifiée.  
  
 MODIFY NAME  **=**  *nouveau_nom_base_de_données*  
 Renomme la base de données portant le nom spécifié en tant que *nouveau_nom_base_de_données*. L’exemple suivant modifie le nom d’une base de données `db1` à `db2`:   

```  
ALTER DATABASE db1  
    MODIFY Name = db2 ;  
```    

 Modifier (édition  **=**  ['base' | « standard » | 'premium' | 'premiumrs'])    
 Modifie le niveau de service de la base de données. L’exemple suivant modifie l’édition à `premium`:
  
```  
ALTER DATABASE current 
    MODIFY (EDITION = 'premium');
``` 

Modification de l’édition échoue si la propriété MAXSIZE de la base de données est définie à une valeur en dehors de la plage valide prise en charge par cette édition.  

 MODIFIER (MAXSIZE  **=**  [100 MO | 500 MO | 1 | 1024... 4096] GO)  
 Spécifie la taille maximale de la base de données. La taille maximale doit être conforme au jeu de valeurs valide pour la propriété EDITION de la base de données. Le fait de modifier la taille maximale de la base de données peut entraîner la modification de la propriété EDITION de la base de données. Le tableau suivant contient la liste des valeurs de MAXSIZE prises en charge et des valeurs par défaut (D) des couches de service [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|**MAXSIZE**|**Basic**|**S0-S2**|**S12 S3**|**P1-P6 et PRS1-PRS6**|**P11-P15**|  
|-----------------|---------------|------------------|-----------------|-----------------|-----------------|-----------------|  
|100 Mo|√|√|√|√|√|  
|250 MO|√|√|√|√|√|  
|500 Mo|√|√|√|√|√|  
|1 Go|√|√|√|√|√|  
|2 Go|√ (D)|√|√|√|√|  
|5 Go|Néant|√|√|√|√|  
|10 GB|Néant|√|√|√|√|  
|20 Go|Néant|√|√|√|√|  
|30 Go|Néant|√|√|√|√|  
|40 Go|Néant|√|√|√|√|  
|50 Go|Néant|√|√|√|√|  
|100 Go|Néant|√|√|√|√|  
|150 Go|Néant|√|√|√|√|  
|200 Go|Néant|√|√|√|√|  
|250 Go|Néant|√ (D)|√ (D)|√|√|  
|300 Go|Néant|√|√|√|√|  
|400 Go|Néant|√|√|√|√|  
|500 Go|Néant|√|√|√ (D)|√|  
|750 GO|Néant|√|√|√|√|  
|1 024 GO|Néant|√|√|√|√ (D)|  
|À partir de 1 024 Go jusqu'à 4096 Go par incréments de 256 Go *|Néant|Néant|Néant|Néant|√|√|  
  
 \*P11 et P15 autorisent MAXSIZE jusqu'à 4 To de 1 024 Go en cours de la taille par défaut.  P11 et P15 peuvent utiliser jusqu'à 4 To de stockage inclus sans frais supplémentaires. Dans le niveau Premium, MAXSIZE supérieure à 1 to n’est actuellement disponible dans les régions suivantes : nous East2, ouest des États-Unis, nous Gov Virginie, Europe de l’ouest, Allemagne Central, Asie du Sud, l’est du Japon, est de l’Australie, Canada Central et est du Canada. Pour connaître les limitations actuelles, consultez [unique des bases de données](https://docs.microsoft.com/azure/sql-database-single-database-resources).  

  
 Les règles suivantes s'appliquent aux arguments MAXSIZE et EDITION.  
  
-   La valeur MAXSIZE, si spécifié, doit être une valeur valide indiquée dans le tableau précédent.  
  
-   Si EDITION est spécifié, mais MAXSIZE n'est pas spécifié, la valeur par défaut de l'édition est utilisée. Par exemple, si EDITION est défini à Standard et que MAXSIZE n'est pas spécifié, MAXSIZE est automatiquement défini à 500 Mo.  
  
-   Si ni MAXSIZE ni EDITION n’est spécifiée, l’édition est définie sur Standard (S0), et MAXSIZE est défini sur 250 Go.  
 

 Modifier (SERVICE_OBJECTIVE = \<objectif de service >)  
 Spécifie le niveau de performances. L’exemple suivant modifie l’objectif d’une base de données premium du service `P6`:
 
```  
ALTER DATABASE current 
    MODIFY (SERVICE_OBJECTIVE = 'P6');
```  
 Les valeurs disponibles pour l’objectif de service sont : `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `PRS1`, `PRS2`, `PRS4`, et `PRS6`. Pour plus d’informations sur la taille, les éditions et les combinaisons d’objectifs de service et les descriptions des objectifs de service, consultez [niveaux de Service de base de données SQL Azure et les niveaux de Performance](http://msdn.microsoft.com/library/azure/dn741336.aspx). Si le SERVICE_OBJECTIVE spécifié n’est pas pris en charge par l’édition, vous recevez une erreur. Si vous voulez modifier la valeur de SERVICE_OBJECTIVE pour passer d'un niveau de service à un autre (par exemple de S1 à P1), vous devrez également modifier la valeur d'EDITION.  
  
 Modifier (SERVICE_OBJECTIVE = élastique\_POOL (nom = \<elastic_pool_name >)  
 Pour ajouter une base de données existante à un pool élastique, la valeur ELASTIC_POOL le SERVICE_OBJECTIVE de la base de données et fournissez le nom du pool élastique. Vous pouvez également utiliser cette option pour modifier la base de données à un autre pool élastique du même serveur. Pour plus d’informations, consultez [créer et gérer un pool élastique de base de données SQL](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/). Pour supprimer une base de données à partir d’un pool élastique, utilisez ALTER DATABASE pour définir le SERVICE_OBJECTIVE à un niveau de performance de base de données unique.  

 Ajouter un serveur secondaire ON \<partner_server_name >  
 Crée une base de données secondaires géo-réplication avec le même nom sur un serveur partenaire, de rendre la base de données local dans une géo-réplication principal et démarre la réplication asynchrone des données à partir du principal vers le nouveau serveur secondaire. Si une base de données portant le même nom existe déjà sur le serveur secondaire, la commande échoue. La commande est exécutée sur la base de données master sur le serveur qui héberge la base de données locale qui devient le serveur principal.  
  
 AVEC ALLOW_CONNECTIONS {TOUTES LES | **NON** }  
 Lorsque ALLOW_CONNECTIONS n’est pas spécifié, il a la valeur NO par défaut. Si elle est définie à tous, il est une base de données en lecture seule qui permet à toutes les connexions avec les autorisations appropriées pour vous connecter.  
  
 AVEC SERVICE_OBJECTIVE {'S0' | 'S1' | « S2 » | « S3 » | 'S4' | 'S6' | 'S7' | 'F9' | 'S12' | « P1 » | « P2 » | 'P4' | 'P6' | 'P11' | 'P15' | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6'}  
 Lorsque SERVICE_OBJECTIVE n’est pas spécifié, la base de données secondaire est créé au même niveau de service en tant que base de données primaire. Lorsque SERVICE_OBJECTIVE est spécifié, la base de données secondaire est créée au niveau spécifié. Cette option prend en charge la création de bases de données secondaires géo-répliquées avec des niveaux de service moins coûteux. Le SERVICE_OBJECTIVE spécifié doit figurer dans la même édition de la source. Par exemple, vous ne pouvez pas spécifier S0 si l’édition premium n’est.  
  
 ELASTIC_POOL (nom = \<elastic_pool_name)  
 Lorsque ELASTIC_POOL n’est pas spécifié, la base de données secondaire n’est pas créé dans un pool élastique. Lorsque ELASTIC_POOL est spécifié, la base de données secondaire est créé dans le pool spécifié.  
  
> [!IMPORTANT]  
>  L’utilisateur qui exécute la commande Ajouter un réplica secondaire doit être DBManager sur le serveur principal, appartenance db_owner dans la base de données locale et DBManager sur le serveur secondaire.  
  
 SUPPRIMER le serveur secondaire ON \<partner_server_name >  
 Supprime la géo-répliquées secondaire base de données spécifiée sur le serveur spécifié. La commande est exécutée sur la base de données master sur le serveur qui héberge la base de données primaire.  
  
> [!IMPORTANT]  
>  L’utilisateur qui exécute la commande Supprimer secondaire doit être DBManager sur le serveur principal.  
  
 FAILOVER  
 Promeut la base de données secondaire en partenariat géo-réplication sur lequel la commande est exécutée pour qu’il devienne le réplica principal et rétrograde le principal actuel pour qu’il devienne le nouveau serveur secondaire. Dans le cadre de ce processus, le mode de géo-réplication temporairement passe du mode asynchrone vers le mode synchrone. Pendant le processus de basculement :  
  
1.  Le réplica principal cesse d’accepter les nouvelles transactions.  
  
2.  Toutes les transactions en attente sont vidées sur le serveur secondaire.  
  
3.  Le serveur secondaire devient le serveur principal et commence la géo-réplication asynchrone avec l’ancien principal / la nouvelle base de données secondaire.  
  
 Cette séquence garantit qu’aucune perte de données se produit. La période pendant laquelle les deux bases de données ne sont pas disponibles est l’ordre de 0-25 secondes tandis que les rôles sont échangés. L’opération total doit pas prendre plue d’une minute environ. Si la base de données primaire n’est pas disponible lors de cette commande est émise, la commande échoue avec un message d’erreur indiquant que la base de données primaire n’est pas disponible. Si le processus de basculement ne se termine pas et il semble bloqué, vous pouvez utiliser la commande de basculement de force et accepter la perte de données - et ensuite, si vous avez besoin de récupérer les données perdues, appelez devops (CSS) pour récupérer les données perdues.  
  
> [!IMPORTANT]  
>  L’utilisateur qui exécute la commande de basculement doit être DBManager sur le serveur principal et le serveur secondaire.  
  
 FORCE_FAILOVER_ALLOW_DATA_LOSS  
 Promeut la base de données secondaire en partenariat géo-réplication sur lequel la commande est exécutée pour qu’il devienne le réplica principal et rétrograde le principal actuel pour qu’il devienne le nouveau serveur secondaire. Utilisez cette commande uniquement lorsque le serveur principal actuel n’est plus disponible. Il est conçu pour la récupération d’urgence, lorsque la restauration de disponibilité est critique, et une perte de données est acceptable.  
  
 Lors d’un basculement forcé :  
  
1.  La base de données secondaire devient la base de données primaire immédiatement et commence à accepter de nouvelles transactions.  
  
2.  Lorsque le serveur principal d’origine puisse se reconnecter avec le nouveau réplica principal, une sauvegarde incrémentielle est effectuée sur la version d’origine principale et le principal d’origine devient une nouvelle base de données secondaire.  
  
3.  Pour récupérer des données à partir de cette sauvegarde incrémentielle sur l’ancien principal, l’utilisateur s’engage devops/CSS.  
  
4.  S’il existe des bases de données secondaires supplémentaires, ils sont automatiquement reconfigurés pour devenir des serveurs secondaires le nouveau réplica principal. Ce processus est asynchrone et il peut y avoir un délai jusqu'à ce que ce processus se termine. Jusqu'à ce que la reconfiguration terminée, les éléments secondaires continuent à être des bases de données secondaires de l’ancien serveur principal.  
  
> [!IMPORTANT]  
>  L’utilisateur exécutant la commande FORCE_FAILOVER_ALLOW_DATA_LOSS doit être DBManager sur le serveur principal et le serveur secondaire.  
  
## <a name="remarks"></a>Notes  
 Pour supprimer une base de données, utilisez [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
  
 Pour réduire la taille d’une base de données, utilisez [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
 L'instruction ALTER DATABASE doit être exécutée en mode de validation automatique (mode de gestion des transactions par défaut) et n'est pas autorisée dans une transaction explicite ou implicite.  
  
 Cette opération entraîne la recompilation de tous les plans d'exécution ultérieurs et peut entraîner une baisse temporaire et brutale des performances des requêtes. Pour chaque mémoire cache effacée dans le cache de plan, le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient le message d'information suivant : « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a rencontré %d occurrence(s) de vidages de mémoire cache pour la mémoire cache '%s' (partie du cache du plan) en raison d'opérations de maintenance ou de reconfiguration de base de données ». Ce message est enregistré toutes les cinq minutes si le cache est vidé au cours de cet intervalle de temps.  
  
 Le cache de procédures est également vidé dans les scénarios suivants :  
  
-   L'option de base de données AUTO_CLOSE est activée (ON). Lorsqu'aucune connexion utilisateur ne fait référence ou n'utilise la base de données, la tâche en arrière-plan essaie de fermer et d'arrêter la base de données automatiquement.  
  
-   Vous exécutez plusieurs requêtes sur une base de données dont les options par défaut sont activées. Puis, la base de données est supprimée.  
  
-   Vous reconstruisez avec succès le journal des transactions d'une base de données.  
  
-   Vous restaurez une sauvegarde de base de données.  
  
-   Vous détachez une base de données.  
  
## <a name="viewing-database-information"></a>Affichage des informations de bases de données  
 Vous pouvez utiliser les affichages catalogue, les fonctions système et les procédures stockées du système pour retourner des informations sur les bases de données, les fichiers et les groupes de fichiers.  
  
## <a name="permissions"></a>Permissions  
 Seule la connexion principale au niveau du serveur (créée par le processus de configuration) ou les membres du rôle de base de données `dbmanager` peuvent modifier une base de données.  
  
> [!IMPORTANT]  
>  Le propriétaire de la base de données ne peut pas modifier la base de données à moins d'être membre du rôle `dbmanager`.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-check-the-edition-options-and-change-them"></a>A. Vérifiez les options d’édition et les modifier :

```
SELECT Edition = DATABASEPROPERTYEX('db1', 'EDITION'),
        ServiceObjective = DATABASEPROPERTYEX('db1', 'ServiceObjective'),
        MaxSizeInBytes =  DATABASEPROPERTYEX('db1', 'MaxSizeInBytes');

ALTER DATABASE [db1] MODIFY (EDITION = 'Premium', MAXSIZE = 1024 GB, SERVICE_OBJECTIVE = 'P15');
```

### <a name="b-moving-a-database-to-a-different-elastic-pool"></a>B. Déplacement d’une base de données vers un autre pool élastique  
 Déplace une base de données existante dans un pool appelé pool1 :  
  
```  
ALTER DATABASE db1   
MODIFY ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = pool1 ) ) ;  
```  
  
### <a name="c-add-a-geo-replication-secondary"></a>C. Ajouter une base de données de géo-réplication secondaire  
 Crée une base de données secondaire non lisible de db1 sur serveur `secondaryserver` de la db1 sur le serveur local.  
  
```  
ALTER DATABASE db1   
ADD SECONDARY ON SERVER secondaryserver   
WITH ( ALLOW_CONNECTIONS = NO )  
```  
  
### <a name="d-remove-a-geo-replication-secondary"></a>D. Supprimer une base de données de géo-réplication secondaire  
 Supprime la base de données secondaire db1 sur serveur `secondaryserver`.  
  
```  
ALTER DATABASE db1   
REMOVE SECONDARY ON SERVER testsecondaryserver   
```  
  
### <a name="e-failover-to-a-geo-replication-secondary"></a>E. Basculement vers une base de données de géo-réplication secondaire  
 Promeut un db1 de base de données secondaire sur le serveur `secondaryserver` pour devenir la base de données primaire exécuté sur le serveur `secondaryserver`.  
  
```  
ALTER DATABASE db1 FAILOVER  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une base de données &#40; Base de données SQL Azure &#41;](../../t-sql/statements/create-database-azure-sql-database.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL &#40; Transact-SQL &#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [Sys.database_mirroring_witnesses &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [Sys.data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [Sys.FileGroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Sys.master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Bases de données système](../../relational-databases/databases/system-databases.md)  
  
  

