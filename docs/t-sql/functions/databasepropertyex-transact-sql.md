---
title: DATABASEPROPERTYEX (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASEPROPERTYEX
- DATABASEPROPERTYEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DATABASEPROPERTYEX function
- displaying database properties
- database properties [SQL Server]
ms.assetid: 8a9e0ffb-28b5-4640-95b2-a54e3e5ad941
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a67b74ad595fdf7b6f3a63dbd2ea2c9e5793f54f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="databasepropertyex-transact-sql"></a>DATABASEPROPERTYEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne le paramètre actuel de l'option ou de la propriété de la base de données spécifiée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATABASEPROPERTYEX ( database , property )  
```  
  
## <a name="arguments"></a>Arguments  
*database*  
Expression qui représente le nom de la base de données pour laquelle l’information sur la propriété nommée doit être retournée. *database* est de type **nvarchar(128)**.  
Pour [!INCLUDE[ssSDS](../../includes/sssds-md.md)], doit être le nom de la base de données actuelle. Retourne la valeur NULL pour toutes les propriétés si un nom de base de données différent est fourni.
  
*property*  
Expression représentant le nom de la propriété de base de données à renvoyer. *property* est de type **varchar(128)** et peut prendre l’une des valeurs suivantes. Le type de retour est **sql_variant**. Le tableau qui suit indique le type de données de base pour chaque valeur de propriété.
  
> [!NOTE]  
>  Si la base de données n'est pas démarrée, les propriétés que le serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] récupère en accédant directement à la base de données, au lieu de récupérer la valeur des métadonnées, retournent NULL. Cette situation se présente lorsque la propriété AUTO_CLOSE de la base de données a la valeur ON ou que la base de données est hors connexion.  
  
|Propriété|Description|Valeur retournée|  
|---|---|---|
|Classement|Nom du classement par défaut de la base de données|Nom du classement<br /><br /> NULL = la base de données n'est pas démarrée.<br /><br /> Type de données de base : **nvarchar(128)**|  
|ComparisonStyle|Style de comparaison Windows du classement. ComparisonStyle est une donnée bitmap calculée à l’aide des valeurs suivantes pour les styles possibles.<br /><br /> Ignorer la casse : 1<br /><br /> Ignorer les accents : 2<br /><br /> Ignorer le type de caractères Kana : 65536<br /><br /> Ignorer la largeur : 131072<br /><br /> <br /><br /> Par exemple, la valeur par défaut 196609 est le résultat de la combinaison des options permettant d'ignorer la casse, le type de caractères Kana et la largeur.|Retourne le style de comparaison.<br /><br /> Renvoie 0 pour tous les classements binaires.<br /><br /> Type de données de base : **int**|  
|Édition|Édition de la base de données ou couche de service.|**S’applique à** : [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].<br /><br /> <br /><br /> Web = Édition Web de la base de données<br /><br /> Business = Édition Business de la base de données<br /><br /> Simple<br /><br /> Standard<br /><br /> Premium<br /><br /> Système (pour la base de données master)<br /><br /> NULL = la base de données n'est pas démarrée.<br /><br /> Type de données de base : **nvarchar**(64)|  
|IsAnsiNullDefault|La base de données suit les règles ISO d'autorisation des valeurs Null.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsAnsiNullsEnabled|Toutes les comparaisons à une valeur NULL produisent le résultat UNKNOWN (inconnu).|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsAnsiPaddingEnabled|Les chaînes sont complétées à la même longueur avant leur comparaison ou insertion.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsAnsiWarningsEnabled|Des messages d'erreur ou d'avertissement sont affichés si des conditions d'erreur standard apparaissent.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsArithmeticAbortEnabled|Une requête s'arrête lorsqu'un dépassement de capacité ou une division par zéro se produit durant son exécution.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsAutoClose|La base de données est fermée correctement et ses ressources sont libérées après la fin de session du dernier utilisateur.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsAutoCreateStatistics|L'optimiseur de requête crée des statistiques de colonnes uniques, selon les besoins, pour améliorer les performances des requêtes.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsAutoCreateStatisticsIncremental|Les statistiques de colonnes uniques créées automatiquement sont incrémentielles lorsque cela est possible.|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsAutoShrink|Les fichiers de base de données peuvent faire l'objet d'une réduction périodique automatique.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsAutoUpdateStatistics|L'optimiseur de requête met à jour les statistiques existantes lorsqu'elles sont utilisées par une requête et qu'elles sont peut-être obsolètes.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|
|IsClone|La base de données est une simple copie du schéma et des statistiques d’une base de données utilisateur.|**S’applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Service Pack 2.<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**| 
|IsCloseCursorsOnCommitEnabled|Les curseurs ouverts lors de la validation d'une transaction sont fermés.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsFulltextEnabled|L'indexation sémantique et de texte intégral est activée pour la base de données.|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**<br /><br /> **Remarque :** La valeur de cette propriété est sans effet. Les bases de données utilisateur sont toujours activées pour la recherche en texte intégral. Cette colonne sera supprimée dans une version future de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser cette colonne dans de nouveaux travaux de développement et modifiez dès que possible les applications qui utilisent actuellement l'une de ces colonnes.|  
|IsInStandBy|La base de données est en ligne en lecture seule, avec la restauration du journal autorisée.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsLocalCursorsDefault|Les déclarations de curseurs prennent la valeur LOCAL par défaut.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsMemoryOptimizedElevateToSnapshotEnabled|L'isolation SNAPSHOT permet d'accéder aux tables optimisées en mémoire lorsque le paramètre de session TRANSACTION ISOLATION LEVEL a une valeur correspondant à un niveau d'isolation inférieur, READ COMMITTED ou READ UNCOMMITTED.|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> Type de données de base : **int**|  
|IsMergePublished|Les tables d'une base de données peuvent être publiées pour la réplication de fusion, si la réplication est installée.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsNullConcat|Un opérande de concaténation Null produit NULL.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsNumericRoundAbortEnabled|Des erreurs sont générées lors d'une perte de précision dans une expression.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsParameterizationForced|L'option SET de base de données PARAMETERIZATION a la valeur FORCED.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide|  
|IsQuotedIdentifiersEnabled|Les guillemets doubles peuvent être utilisés dans les identificateurs.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsPublished|Les tables de la base de données peuvent être publiées pour la réplication transactionnelle ou d'instantané, si la réplication est installée.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsRecursiveTriggersEnabled|Le fonctionnement récursif des déclencheurs est activé.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsSubscribed|La base de données est abonnée à une publication.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsSyncWithBackup|La base de données est soit une base de données publiée, soit une base de données de distribution ; en outre, elle peut être restaurée sans interrompre la réplication transactionnelle.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsTornPageDetectionEnabled|Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] détecte les opérations d'E/S interrompues à la suite d'une coupure de courant ou de toute autre panne du système.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = entrée non valide<br /><br /> Type de données de base : **int**|  
|IsXTPSupported|Indique si la base de données prend en charge l’option OLTP en mémoire, à savoir la création et l’utilisation de tables à mémoire optimisée et de modules compilés en mode natif.<br /><br /> Spécifique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :<br /><br /> La propriété IsXTPSupported est indépendante de l’existence de tout groupe de fichiers MEMORY_OPTIMIZED_DATA, qui est nécessaire pour la création d’objets OLTP en mémoire.|**S’applique à** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br /> **S’applique à** : [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] depuis [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].<br /><br /> <br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide, non applicable, ou erreur<br /><br /> Type de données de base : **int**|  
|LCID|Identificateur des paramètres régionaux (LCID) Windows du classement.|Valeur LCID (au format décimal).<br /><br /> Type de données de base : **int**|  
|MaxSizeInBytes|Taille maximale de la base de données en octets.|**S’applique à** : [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].<br /><br /> <br /><br /> 1073741824<br /><br /> 5368709120<br /><br /> 10737418240<br /><br /> 21474836480<br /><br /> 32212254720<br /><br /> 42949672960<br /><br /> 53687091200<br /><br /> NULL = Base de données non démarrée<br /><br /> Type de données de base : **bigint**|  
|Récupération|Mode de récupération de la base de données|FULL = mode de récupération complète<br /><br /> BULK_LOGGED = mode de récupération utilisant les journaux de transactions<br /><br /> SIMPLE = mode de récupération simple<br /><br /> Type de données de base : **nvarchar(128)**|  
|ServiceObjective|Décrit le niveau de performance de la base de données dans [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ou [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].|Les valeurs possibles sont les suivantes :<br /><br /> NULL : base de données non démarrée<br /><br /> Shared (pour l'édition Web/Business)<br /><br /> Simple<br /><br /> S0<br /><br /> S1<br /><br /> S2<br /><br /> S3<br /><br /> P1<br /><br /> P2<br /><br /> P3<br /><br /> ElasticPool<br /><br /> Système (pour base de données master)<br /><br /> Type de données de base : **nvarchar(32)**|  
|ServiceObjectiveId|ID de l'objectif de service dans la [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|**uniqueidentifier** qui identifie l’objectif de service.|  
|SQLSortOrder|ID d'ordre de tri [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pris en charge dans les versions antérieures de SQL Server.|0 = la base de données utilise le classement Windows<br /><br /> >0 = ID d'ordre de tri [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> NULL = entrée non valide ou la base de données n'est pas démarrée<br /><br /> Type de données de base : **tinyint**|  
|État|État de la base de données.|ONLINE = la base de données est disponible pour la requête.<br /><br /> **Remarque :** L’état ONLINE peut être retourné tant que la base de données est ouverte et pas encore récupérée. Pour déterminer lorsqu’une base de données peut accepter les connexions, interrogez la propriété Collation de **DATABASEPROPERTYEX**. La base de données peut accepter les connexions lorsque le classement de base de données retourne une valeur non NULL. Pour les bases de données AlwaysOn, interrogez les colonnes database_state ou database_state_desc de sys.dm_hadr_database_replica_states.<br /><br /> OFFLINE = la base de données a été explicitement mise hors connexion.<br /><br /> RESTORING = la base de données est en cours de restauration.<br /><br /> RECOVERING = la base de données est en cours de récupération et n'est toujours pas disponible pour les requêtes.<br /><br /> SUSPECT = la base de données n'a pas été récupérée.<br /><br /> EMERGENCY = la base de données se trouve dans un état d'urgence en lecture seule. L'accès est limité aux membres sysadmin.<br /><br /> Type de données de base : **nvarchar(128)**|  
|Updateability|Indique si les données peuvent être modifiées.|READ_ONLY = les données peuvent être lues mais pas modifiées.<br /><br /> READ_WRITE = les données peuvent être lues et modifiées.<br /><br /> Type de données de base : **nvarchar(128)**|  
|UserAccess|Définit les utilisateurs autorisés à accéder à la base de données.|SINGLE_USER = un seul utilisateur db_owner, dbcreator ou sysadmin à la fois<br /><br /> RESTRICTED_USER = seuls les membres des rôles db_owner, dbcreator et sysadmin<br /><br /> MULTI_USER = tous les utilisateurs<br /><br /> Type de données de base : **nvarchar(128)**|  
|Options de version|Numéro de version interne du code [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec lequel la base de données a été créée. [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|Numéro de version = la base de données est ouverte.<br /><br /> NULL = la base de données n'est pas démarrée.<br /><br /> Type de données de base : **int**|  
  
## <a name="return-types"></a>Types de retour
**sql_variant**
  
## <a name="exceptions"></a>Exceptions  
Retourne la valeur NULL en cas d'erreur ou si un appelant n'est pas autorisé à afficher l'objet.
  
Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un utilisateur peut voir uniquement les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d'un droit d'accès. Cela signifie que les fonctions intégrées générant des métadonnées, telles que OBJECT_ID, peuvent retourner la valeur NULL si l'utilisateur ne dispose d'aucune autorisation sur l'objet. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Notes   
DATABASEPROPERTYEX retourne un seul paramètre de propriété à la fois. Pour afficher plusieurs paramètres de propriété, utilisez la vue de catalogue [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).
  
## <a name="examples"></a>Exemples  
  
### <a name="a-retrieving-the-status-of-the-autoshrink-database-option"></a>A. Récupération de l'état de l'option de base de données AUTO_SHRINK  
L'exemple suivant retourne l'état de l'option de base de données AUTO_SHRINK de la base de données `AdventureWorks`.
  
```sql
SELECT DATABASEPROPERTYEX('AdventureWorks2014', 'IsAutoShrink');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)] Cela indique que la base de données AUTO_SHRINK est désactivée.
  
```sql
------------------  
0  
```  
  
### <a name="b-retrieving-the-default-collation-for-a-database"></a>B. Récupération du classement par défaut d'une base de données  
L’exemple suivant retourne plusieurs attributs de la base de données `AdventureWorks`.
  
```sql
SELECT   
    DATABASEPROPERTYEX('AdventureWorks2014', 'Collation') AS Collation,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'Edition') AS Edition,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'ServiceObjective') AS ServiceObjective,  
    DATABASEPROPERTYEX('AdventureWorks2014', 'MaxSizeInBytes') AS MaxSizeInBytes  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Collation                     Edition        ServiceObjective  MaxSizeInBytes  
----------------------------  -------------  ----------------  --------------  
SQL_Latin1_General_CP1_CI_AS  DataWarehouse  DW1000            5368709120  
```  
  
## <a name="see-also"></a>Voir aussi
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[États d’une base de données](../../relational-databases/databases/database-states.md)  
[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
[sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)
  
  
