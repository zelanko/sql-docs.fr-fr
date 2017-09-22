---
title: "MODIFIER la CONFIGURATION inclus dans l’étendue de base de données (Transact-SQL) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ALTER_DATABASE_SCOPED_CONFIGURATION
- ALTER_DATABASE_SCOPED_CONFIGURATION_TSQL
- DATABASE_SCOPED_CONFIGURATION_TSQL
- SCOPED_CONFIGURATION_TSQL
- SCOPED_TSQL
- ALTER_DATABASE_SCOPED_TSQL
- DATABASE_SCOPED_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CONFIGURATION statement
- configuration [SQL Server], ALTER DATABASE SCOPED CONFIGURATION statement
ms.assetid: 63373c2f-9a0b-431b-b9d2-6fa35641571a
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 0fbb1f0699328a59749e5bba7efd7661e9b36e5a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="alter-database-scoped-configuration-transact-sql"></a>MODIFIER la CONFIGURATION inclus dans l’étendue de base de données (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cette instruction permet plusieurs paramètres de configuration de base de données à la **base de données individuelle** niveau. Cette instruction n’est disponible dans les deux [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] et dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Ces paramètres sont :  
  
- Effacer le cache de procédures.  
  
- Affecter au paramètre MAXDOP une valeur arbitraire (1, 2, etc.) adaptée à la base de données primaire et affecter une autre valeur (par exemple, 0) à toutes les bases de données secondaires utilisées (par exemple, pour les requêtes de rapport).  
  
- Définir le modèle d’estimation de la cardinalité de l’optimiseur de requête indépendant de la base de données au niveau de compatibilité.  
  
- Activer ou désactiver la détection de paramètres au niveau de la base de données.
  
- Activer ou désactiver les correctifs d’optimisation des requêtes au niveau de la base de données.

- Activer ou désactiver le cache d’identité au niveau de la base de données.
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER DATABASE SCOPED CONFIGURATION  
{        
     {  [ FOR SECONDARY] SET <set_options>  }    
}  
| CLEAR PROCEDURE_CACHE  
| SET IDENTITY_CACHE = { ON | OFF }
[;]    
  
< set_options > ::=    
{  
    MAXDOP = { <value> | PRIMARY}    
    | LEGACY_CARDINALITY_ESTIMATION = { ON | OFF | PRIMARY}    
    | PARAMETER_SNIFFING = { ON | OFF | PRIMARY}    
    | QUERY_OPTIMIZER_HOTFIXES = { ON | OFF | PRIMARY}    
}  
  
```  
  
## <a name="arguments"></a>Arguments  
 
BASE DE DONNÉES SECONDAIRE  
 
Spécifie les paramètres pour les bases de données secondaires (toutes les bases de données secondaire doivent avoir des valeurs identiques).  
  
MAXDOP ** = ** {\<valeur > | PRINCIPAL}  
**\<valeur >**  
  
Spécifie la valeur par défaut MAXDOP qui doit être utilisé pour les instructions. 0 est la valeur par défaut et indique que la configuration du serveur doit être utilisée à la place. Se substitue à la MAXDOP dans l’étendue de la base de données (sauf si elle est définie sur 0) la **degré maximal de parallélisme** définie au niveau du serveur par sp_configure. Indicateurs de requête peuvent tout de même remplacer la base de données étendue MAXDOP afin de paramétrer des requêtes spécifiques qui nécessitent des paramètres différents. Tous ces paramètres sont limitées par le MAXDOP définie pour le groupe de charges de travail.   

Vous pouvez utiliser l'option max degree of parallelism pour limiter le nombre de processeurs à utiliser lors de l'exécution des plans parallèles. SQL Server considère que les plans d’exécution parallèle pour les requêtes, les opérations d’index data definition language (DDL), insertion parallèle, la colonne collectiion de statistiques parallèle et remplissage des curseurs statiques et pilotés par la modification en ligne.
 
Pour définir cette option au niveau de l’instance, consultez [configurer le degré maximal de parallélisme Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). 

> [!TIP] 
> Pour ce faire, au niveau de la requête, ajoutez le **MAXDOP** [indicateur de requête](../../t-sql/queries/hints-transact-sql-query.md).  
  
PRIMARY  
  
Peut être défini que pour les bases de données secondaires, lors de la base de données sur le serveur principal et indique que la configuration est celui défini pour le serveur principal. Si la configuration pour que les modifications principales, la valeur sur les bases de données secondaires sera modifiée en conséquence sans avoir besoin de définir les éléments secondaires de valeur explicitement. **PRINCIPAL** est le paramètre par défaut pour les bases de données secondaires.  
  
LEGACY_CARDINALITY_ESTIMATION ** = ** {ON | **OFF** | PRINCIPAL}  

Permet de définir le modèle d’estimation de cardinalité d’optimiseur de requête pour le SQL Server 2012 et version antérieure indépendantes du niveau de compatibilité de la base de données. La valeur par défaut est **OFF**, les jeux de modèle d’estimation de cardinalité d’optimiseur de requête basé sur le niveau de compatibilité de la base de données. Définir cette valeur sur **ON** équivaut à activer [indicateur de Trace 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). 

> [!TIP] 
> Pour ce faire, au niveau de la requête, ajoutez le **QUERYTRACEON** [indicateur de requête](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). En commençant par [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, pour effectuer cette opération au niveau de la requête, ajoutez le **indicateur USE** [indicateur de requête](../../t-sql/queries/hints-transact-sql-query.md) au lieu d’utiliser l’indicateur de trace. 
  
PRIMARY  
  
Cette valeur est valide uniquement sur les bases de données secondaires lors de la base de données sur le serveur principal et spécifie que le paramètre de modèle de requête optimizer cardinalité estimation sur toutes les bases de données secondaires est la valeur définie pour le serveur principal. Si la configuration sur le serveur principal pour le modèle d’estimation de cardinalité d’optimiseur de requête est modifiée, la valeur sur les bases de données secondaires changent en conséquence. **PRINCIPAL** est le paramètre par défaut pour les bases de données secondaires.  
  
PARAMETER_SNIFFING ** = ** { **ON** | DÉSACTIVER | PRINCIPAL}  

Active ou désactive [la détection des paramètres](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing). La valeur par défaut est ON. Cette propriété est équivalente à l’ [indicateur de trace 4136](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   

> [!TIP] 
> Pour ce faire, au niveau de la requête, consultez la **OPTIMIZE FOR UNKNOWN** [indicateur de requête](../../t-sql/queries/hints-transact-sql-query.md). En commençant par [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, pour effectuer cette opération au niveau de la requête, le **indicateur USE** [indicateur de requête](../../t-sql/queries/hints-transact-sql-query.md) est également disponible. 
  
PRIMARY  
  
Cette valeur est valide uniquement sur les bases de données secondaires lors de la base de données sur le serveur principal et spécifie que la valeur de ce paramètre sur tous les réplicas secondaires est la valeur définie pour le serveur principal. Si la configuration sur le serveur principal pour l’utilisation de [la détection des paramètres](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing) change, la valeur sur les bases de données secondaires change en conséquence, sans avoir besoin de définir les éléments secondaires valeur explicitement. Il s’agit du paramètre par défaut pour les bases de données secondaires.  
  
QUERY_OPTIMIZER_HOTFIXES ** = ** {ON | **OFF** | PRINCIPAL}  

Active ou désactive les correctifs logiciels de l’optimisation de requête, quelle que soit le niveau de compatibilité de la base de données. La valeur par défaut est **OFF**. Cela équivaut à activer [indicateur de Trace 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   

> [!TIP] 
> Pour ce faire, au niveau de la requête, ajoutez le **QUERYTRACEON** [indicateur de requête](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). En commençant par [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, pour effectuer cette opération au niveau de la requête, ajoutez l’indicateur USE [indicateur de requête](../../t-sql/queries/hints-transact-sql-query.md) au lieu d’utiliser l’indicateur de trace.  
  
PRIMARY  
  
Cette valeur est valide uniquement sur les bases de données secondaires lors de la base de données sur le serveur principal et spécifie que la valeur de ce paramètre sur tous les réplicas secondaires est la valeur définie pour le serveur principal. Si la configuration pour que les modifications principales, la valeur sur les bases de données secondaires sera modifiée en conséquence sans avoir besoin de définir les éléments secondaires de valeur explicitement. Il s’agit du paramètre par défaut pour les bases de données secondaires.  
  
DÉSACTIVEZ PROCEDURE_CACHE  

Efface le cache de procédure pour la base de données. Cela peut être exécutée à la fois sur le serveur principal et les bases de données secondaires.  

IDENTITY_CACHE = { **ON** | {OFF}  

**S’applique à**: SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique) 

Active ou désactive le cache d’identité au niveau de la base de données. La valeur par défaut est **ON**. La mise en cache d’identité est utilisé pour améliorer les performances d’insertion sur des tables avec colonnes Identity. Pour éviter les écarts dans les valeurs de la colonne d’identité dans les cas où le serveur redémarre de façon inattendue ou bascule vers un serveur secondaire, désactivez l’option IDENTITY_CACHE. Cette option est similaire à l’existant SQL Server Trace indicateur 272, sauf qu’elle peut être définie au niveau de la base de données plutôt qu’uniquement au niveau du serveur.   

> [!NOTE] 
> Cette option peut uniquement être définie pour le serveur principal. Pour plus d’informations, consultez [les colonnes d’identité](create-table-transact-sql-identity-property.md).  
>

##  <a name="Permissions"></a> Autorisations  
 Requiert ALTER toute CONFIGURATION de l’étendue de base de données   
sur la base de données. Cette autorisation peut être accordée par un utilisateur avec l’autorisation CONTROL sur une base de données  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Vous pouvez configurer des bases de données secondaires pour tous les paramètres de configuration d’étendues différentes de leur principal, toutes les bases de données secondaire utilisera la même configuration. Impossible de configurer des paramètres différents pour des bases de données secondaires.  
  
 L’exécution de cette instruction supprime le cache de procédure dans la base de données en cours, ce qui signifie que toutes les requêtes doivent recompiler.  
  
 Pour les requêtes de nom en 3 parties, les paramètres pour la connexion de base de données actuelle pour la requête seront pris en compte, autres que pour les modules SQL (par exemple, les procédures, fonctions et déclencheurs) qui sont compilés dans le contexte actuel de la base de données et par conséquent, utilisez les options de la base de données dans lesquels ils résident.  
  
 L’événement ALTER_DATABASE_SCOPED_CONFIGURATION est ajouté comme un événement DDL qui peut être utilisé pour activer un déclencheur DDL. Il s’agit d’un enfant du groupe de déclencheur ALTER_DATABASE_EVENTS.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 **MAXDOP**  
  
 Les paramètres de niveau de granularité peuvent remplacer celles globales et que le gouverneur de ressources peut couvrir tous les autres paramètres MAXDOP.  La logique pour le paramètre MAXDOP est la suivante :  
  
-   Indicateur de requête remplace sp_configure et la base de données étendue de configuration. Si le groupe de ressources MAXDOP est défini pour le groupe de charges de travail :  
  
    -   Si l’indicateur de requête est définie sur 0, il est remplacé par la configuration du gouverneur de ressources.  
  
    -   Si l’indicateur de requête est différente de 0, elle est limitée par la configuration du gouverneur de ressources.  
  
-   La base de données d’une étendue paramètre (sauf si elle est 0) remplace le paramètre sp_configure, sauf s’il existe un indicateur de requête et est limitée par la configuration du gouverneur de ressources.  
  
-   Le paramètre sp_configure est remplacé par la configuration du gouverneur de ressources.  
  
 **QUERY_OPTIMIZER_HOTFIXES**  
  
 Lorsque l’indicateur QUERYTRACEON est utilisé pour activer l’optimiseur de requête héritées ou les correctifs logiciels optimiseur de requête, il serait une condition OR entre l’indicateur de requête et de la configuration de base de données applique la définition, ce qui signifie que si l’option est activée, les options s’appliquent.  
  
 **GeoDR**  
  
 Lisibles secondaire bases de données, par exemple, les groupes de disponibilité AlwaysOn et géo-réplication du, utilisent la valeur secondaire en vérifiant l’état de la base de données. Bien que nous ne pas recompiler lors du basculement et techniquement le nouveau réplica principal avec des requêtes qui utilisent les paramètres secondaires, l’idée est que le paramètre entre les principaux et secondaires uniquement varient lorsque la charge de travail est différent et par conséquent, les requêtes mises en cache sont à l’aide des paramètres optimaux, tandis que les nouvelles requêtes récupérera les nouveaux paramètres qui sont appropriés pour eux.  
  
 **DacFx**  
  
 ALTER DATABASE SCOPED CONFIGURATION étant une nouvelle fonctionnalité de base de données SQL Azure et SQL Server 2016 qui affecte le schéma de base de données, les exportations du schéma (avec ou sans données) ne sera pas peuvent être importés dans une version antérieure de SQL Server, par exemple, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou < C2 > [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] . Par exemple, une exportation vers un [DACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_3) ou un [BACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_4) à partir d’un [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ou [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] utilisé cette nouvelle fonctionnalité de base de données ne peut pas être importé dans un serveur de bas niveau.  
  
## <a name="metadata"></a>Métadonnées  

Le [sys.database_scoped_configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) vue système fournit des informations sur les configurations de l’étendue dans une base de données. Options de configuration étendue à la base de données apparaissent seulement dans des sys.database_scoped_configurations lorsqu’ils sont des remplacements pour les paramètres par défaut des serveurs. Le [sys.configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) vue système affiche uniquement les paramètres au niveau du serveur.  
  
## <a name="examples"></a>Exemples  
Ces exemples illustrent l’utilisation de ALTER DATABASE SCOPED CONFIGURATION  
  
### <a name="a-grant-permission"></a>A. Accorder l’autorisation  

Cet exemple montre comment accorder l’autorisation nécessaire à l’exécution de ALTER DATABASE SCOPED CONFIGURATION     
à l’utilisateur [Joe].  
  
```tsql  
GRANT ALTER ANY DATABASE SCOPED CONFIGURATION to [Joe] ;  
```  
  
### <a name="b-set-maxdop"></a>B. Jeu de MAXDOP  

Cet exemple définit MAXDOP = 1 pour une base de données primaire et le MAXDOP = 4 pour la base de données secondaire dans un scénario de géo-réplication.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET MAXDOP = 1 ;  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=4 ;  
```  
  
Cet exemple définit MAXDOP pour une base de données secondaire pour être la même qu’il est défini pour sa base de données primaire dans un scénario de géo-réplication.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY ;
```  
  
### <a name="c-set-legacycardinalityestimation"></a>C. Jeu LEGACY_CARDINALITY_ESTIMATION  

Cet exemple affecte LEGACY_CARDINALITY_ESTIMATION à une base de données secondaire dans un scénario de géo-réplication.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=ON ;  
```  
  
Cet exemple définit LEGACY_CARDINALITY_ESTIMATION pour une base de données secondaire, car il s’agit de sa base de données primaire dans un scénario de géo-réplication.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=PRIMARY ;  
```  
  
### <a name="d-set-parametersniffing"></a>D. Jeu PARAMETER_SNIFFING  

Cet exemple définit PARAMETER_SNIFFING Off pour une base de données primaire dans un scénario de géo-réplication.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET PARAMETER_SNIFFING =OFF ;  
```  
  
Cet exemple définit PARAMETER_SNIFFING Off pour une base de données primaire dans un scénario de géo-réplication.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=OFF ;  
```  
  
Cet exemple définit PARAMETER_SNIFFING pour la base de données secondaire, car il est sur la base de données primaire   
dans un scénario de géo-réplication.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING =PRIMARY ;  
```  
  
### <a name="e-set-queryoptimizerhotfixes"></a>E. Jeu QUERY_OPTIMIZER_HOTFIXES  

La valeur QUERY_OPTIMIZER_HOTFIXES ON pour la base de données primaire   
dans un scénario de géo-réplication.  

```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET QUERY_OPTIMIZER_HOTFIXES=ON ;  
```  
  
### <a name="f-clear-procedure-cache"></a>F. Effacer le Cache de procédure  

Cet exemple efface le cache de procédure (possible uniquement pour une base de données primaire).  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE ;  
```  

### <a name="g-set-identitycache"></a>G. Jeu IDENTITY_CACHE

**S’applique à**: SQL Server 2017 et Azure SQL Database (fonctionnalité est en version préliminaire publique) 

Cet exemple désactive le cache d’identité.

```tsql 
ALTER DATABASE SCOPED CONFIGURATION SET IDENTITY_CACHE=OFF ; 
```

## <a name="additional-resources"></a>Ressources supplémentaires

### <a name="maxdop-resources"></a>Ressources MAXDOP 
* [Recommandations et des instructions pour l’option de configuration « max degree of parallelism » dans SQL Server](https://support.microsoft.com/en-us/kb/2806535) 

### <a name="legacycardinalityestimation-resources"></a>Ressources LEGACY_CARDINALITY_ESTIMATION    
* [Estimation de cardinalité (SQL Server)](/sql-docs/docs/relational-databases/performance/cardinality-estimation-sql-server)
* [Optimizing Your Query Plans with the SQL Server 2014 Cardinality Estimator](https://msdn.microsoft.com/library/dn673537.aspx) (Optimisation de vos plans de requête avec l’estimateur de cardinalité SQL Server 2014)

### <a name="parametersniffing-resources"></a>Ressources PARAMETER_SNIFFING    
* [« Il y a un paramètre ! »](https://blogs.msdn.microsoft.com/queryoptteam/2006/03/31/i-smell-a-parameter/)

### <a name="queryoptimizerhotfixes-resources"></a>Ressources QUERY_OPTIMIZER_HOTFIXES    
* [SQL Server modèle optimiseur de requête correctif trace indicateur 4199 maintenance](https://support.microsoft.com/en-us/kb/974006)

## <a name="more-information"></a>Informations complémentaires  
 [Sys.database_scoped_configurations &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)   
 [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [Affichages catalogue de bases de données et de fichiers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Indicateurs de trace &#40; Transact-SQL &#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)   
 [Sys.configurations &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)  
  
  

