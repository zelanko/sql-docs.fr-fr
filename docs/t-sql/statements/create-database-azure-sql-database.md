---
title: "CRÉER la base de données (base de données SQL Azure) | Documents Microsoft"
ms.custom: 
ms.date: 08/28/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SERVICE_OBJECTIVE
- SERVICE_OBJECTIVE_TSQL
- ELASTIC_POOL
- ELASTIC_POOL_TSQL
- EDITION
- EDITION_TSQL
- MAXSIZE
- MAXSIZE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- SERVICE_OBJECTIVE
- ELASTIC_POOL
- EDITION SQL Database
- MAXSIZE SQL Database
ms.assetid: 22b167f7-ae86-490b-adb3-ec02ca1c1508
caps.latest.revision: "62"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c2a8612af978c6cd32056ff192e0eae8909b50cb
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="create-database-azure-sql-database"></a>CREATE DATABASE (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Crée une base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
``` 
  
CREATE DATABASE database_name [ COLLATE collation_name ]  
{  
   (<edition_options> [, ...n])   
}  

[ WITH CATALOG_COLLATION = { DATABASE_DEFAULT | SQL_Latin1_General_CP1_CI_AS }  ]
  
<edition_options> ::=   
{  

      MAXSIZE = { 100 MB | 250 MB | 500 MB | 1 … 1024 … 4096 GB }    
    | ( EDITION = {  'basic' | 'standard' | 'premium' | 'premiumrs'}   
    | SERVICE_OBJECTIVE =   
          {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' | 
            | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'  
            | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' 
            | { ELASTIC_POOL(name = <elastic_pool_name>) } }  ) 
}  

 [;]  
  

```  

```
To copy a database:  
CREATE DATABASE database_name  
    AS COPY OF [source_server_name.] source_database_name  
    [ ( SERVICE_OBJECTIVE =   
          {  'basic' | 'S0' | 'S1' | 'S2' | 'S3' | 'S4'| 'S6'| 'S7'| 'S9'| 'S12' |  
            | 'P1' | 'P2' | 'P4'| 'P6' | 'P11' | 'P15'  
            | 'PRS1' | 'PRS2' | 'PRS4' | 'PRS6' 
            | { ELASTIC_POOL(name = <elastic_pool_name>) } } )  
    ]  
 [;] 
 
```  
  
## <a name="arguments"></a>Arguments  
 Ce diagramme de syntaxe montre les arguments pris en charge dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 *database_name*  
 Nom de la nouvelle base de données. Ce nom doit être unique sur le serveur SQL, qui peut héberger à la fois [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] bases de données et [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] des bases de données et doit respecter le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] règles applicables aux identificateurs. Pour plus d’informations, consultez [identificateurs](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
 *Collation_name*  
 Indique le classement par défaut de la base de données. Le nom du classement peut être un nom de classement Windows ou SQL. S'il est omis, le classement par défaut, SQL_Latin1_General_CP1_CI_AS, est affecté à la base de données.  
  
 Pour plus d’informations sur les noms de classements Windows et SQL, [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
 *CATALOG_COLLATION*  
Spécifie le classement par défaut pour le catalogue de métadonnées. *DATABASE_DEFAULT* Spécifie que le catalogue de métadonnées utilisé pour les vues et tables système assemblées pour faire correspondre le classement par défaut pour la base de données système.  Il s’agit du comportement de SQL Server. 

*SQL_Latin1_General_CP1_CI_AS* Spécifie que le catalogue de métadonnées utilisé pour les vues et tables système être assemblés à un classement SQL_Latin1_General_CP1_CI_AS fixe.  Il s’agit du paramètre par défaut sur la base de données SQL Azure si non spécifié.

 *ÉDITION*  
 Spécifie la couche de service de la base de données. Les valeurs disponibles sont : 'base', 'standard', 'premium' et 'premiumrs'.  
  
 Lorsque EDITION est spécifié mais MAXSIZE n’est pas spécifié, MAXSIZE est défini sur la taille la plus restrictive qui prend en charge de l’édition.  
  
 *MAXSIZE*  
 Spécifie la taille maximale de la base de données. MAXSIZE doit être valide pour l'EDITION (niveau de service) spécifiée. Voici les valeurs de MAXSIZE prises en charge et les valeurs par défaut (D) des niveaux de service.  
  
|**MAXSIZE**|**Basic**|**S0-S2**|**S12 S3**|**P1-P6 et PRS1-PRS6**| **P11-P15** 
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
|300 Go|Néant|Néant|√|√|√|  
|400 Go|Néant|Néant|√|√|√|
|500 Go|Néant|Néant|√|√ (D)|√|
|750 GO|Néant|Néant|√|√|√|
|1 024 GO|Néant|Néant|√|√|√ (D)|
|À partir de 1 024 Go jusqu'à 4096 Go par incréments de 256 Go * |Néant|Néant|Néant|Néant|√|√|  
  
 \*P11 et P15 autorisent MAXSIZE jusqu'à 4 To de 1 024 Go en cours de la taille par défaut.  P11 et P15 peuvent utiliser jusqu'à 4 To de stockage inclus sans frais supplémentaires. Dans le niveau Premium, MAXSIZE supérieure à 1 to n’est actuellement disponible dans les régions suivantes : nous East2, ouest des États-Unis, nous Gov Virginie, Europe de l’ouest, Allemagne Central, Asie du Sud, l’est du Japon, est de l’Australie, Canada Central et est du Canada. Pour connaître les limitations actuelles, consultez [unique des bases de données](https://docs.microsoft.com/azure/sql-database-single-database-resources).  
  
 Les règles suivantes s'appliquent aux arguments MAXSIZE et EDITION.  
  
-   La valeur MAXSIZE, si spécifiée, doit être une valeur valide indiquée dans le tableau ci-dessus.  
  
-   Si EDITION est spécifié, mais MAXSIZE n'est pas spécifié, la valeur par défaut de l'édition est utilisée. Par exemple, si l’édition est définie sur Standard, et MAXSIZE n’est pas spécifié, puis MAXSIZE est automatiquement défini à 250 Mo.  
  
-   Si ni MAXSIZE ni EDITION n’est spécifiée, l’édition est définie sur Standard (S0), et MAXSIZE est défini sur 250 Go.  
  
 SERVICE_OBJECTIVE  
 Spécifie le niveau de performances. Pour plus d’informations sur la taille, les éditions et les combinaisons d’objectifs de service et les descriptions des objectifs de service, consultez [niveaux de Service de base de données SQL Azure et les niveaux de Performance](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/) et [des ressources de base de données SQL limites](https://azure.microsoft.com/documentation/articles/sql-database-resource-limits). Si le SERVICE_OBJECTIVE spécifié n'est pas pris en charge par l'EDITION, un message d'erreur s'affiche.  
  
 ELASTIC_POOL (nom = \<elastic_pool_name >) pour créer une nouvelle base de données dans un pool élastique de base de données, la valeur ELASTIC_POOL le SERVICE_OBJECTIVE de la base de données et fournissez le nom du pool. Pour plus d’informations, consultez [créer et gérer un pool élastique de base de données SQL (aperçu)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/).  
  
 *En tant que copie de [source_server_name.] nom_base_de_données_source*  
 Pour la copie d'une base de données sur le même serveur ou sur un serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] différent.  
  
 *Nom_serveur_source*  
 Nom du serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] où se trouve la base de données source. Ce paramètre est facultatif lorsque la base de données source et la base de données de destination se trouveront sur le même serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Remarque : l'argument `AS COPY OF` ne prend pas en charge les noms de domaine complets uniques. En d'autres termes, si le nom de domaine complet de votre serveur est `serverName.database.windows.net`, utilisez uniquement `serverName` pendant la copie de base de données.  
  
 *nom_base_de_données_source*  
 Nom de la base de données copiée.  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]ne prend pas en charge les arguments et options suivants lors de l’utilisation du `CREATE DATABASE` instruction :  
  
-   Les paramètres relatifs à l’emplacement physique du fichier, tel que \<filespec > et \<groupe de fichiers >  
  
-   Options d'accès externe, telles que DB_CHAINING et TRUSTWORTHY  
  
-   Attachement d'une base de données  
  
-   Options de Service Broker, telles que ENABLE_BROKER, NEW_BROKER et ERROR_BROKER_CONVERSATIONS  
  
-   Instantané de base de données  
  
 Pour plus d’informations sur les arguments et la `CREATE DATABASE` instruction, consultez [CREATE DATABASE &#40; SQL Server Transact-SQL &#41; ](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="remarks"></a>Notes   
 Les bases de données dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] ont plusieurs paramètres par défaut définis lors de la création de la base de données. Pour plus d’informations sur ces paramètres par défaut, consultez la liste de valeurs dans [DATABASEPROPERTYEX &#40; Transact-SQL &#41; ](../../t-sql/functions/databasepropertyex-transact-sql.md).  
  
 MAXSIZE permet de limiter la taille de la base de données. Si la taille de la base de données atteint sa valeur MAXSIZE, vous recevez le code d’erreur 40544. Lorsque cela se produit, vous ne pouvez pas insérer ou mettre à jour des données, ni créer des objets (tels que des tables, des procédures stockées, des vues et des fonctions). Toutefois, vous pouvez encore lire et supprimer des données, tronquer des tables, supprimer des tables et des index et reconstruire des index. Vous pouvez ensuite mettre à jour MAXSIZE avec une valeur supérieure à votre taille de base de données actuelle ou supprimer certaines données afin de libérer de l'espace de stockage. Vous devrez peut-être patienter jusqu'à quinze minutes avant de pouvoir insérer de nouvelles données.  
  
> [!IMPORTANT]  
>  L'instruction `CREATE DATABASE` doit être la seule instruction dans un lot [!INCLUDE[tsql](../../includes/tsql-md.md)]. 
  
 Pour modifier la taille, Édition ou valeurs d’objectif de service ultérieurement, utilisez [ALTER DATABASE &#40; Base de données SQL Azure &#41; ](../../t-sql/statements/alter-database-azure-sql-database.md).  

L’argument CATALOG_COLLATION est uniquement disponible lors de la création de base de données. 
  
## <a name="database-copies"></a>Copies de bases de données  
 Copie une base de données à l’aide de la `CREATE DATABASE` instruction est une opération asynchrone. Par conséquent, une connexion au serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] n'est pas nécessaire pendant toute la durée du processus de copie. La `CREATE DATABASE` instruction retourne le contrôle à l’utilisateur après la création de l’entrée dans sys.databases mais avant la copie de base de données, l’opération est terminée. Autrement dit, l'instruction `CREATE DATABASE` est renvoyée avec succès lorsque la copie de base de données est encore en cours.  
  
-   Analyse le processus de copie sur un [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] serveur : requête le `percentage_complete` ou `replication_state_desc` colonnes dans le [dm_database_copies](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md) ou `state` colonne dans la **sys.databases** vue. Le [sys.dm_operation_status](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md) vue peut être utilisée comme, car elle retourne l’état des opérations de base de données, y compris la copie de base de données.  
  
 Lorsque le processus de copie est terminé avec succès, la base de données de destination est cohérente avec la base de données source au niveau des transactions.  
  
 La syntaxe et les règles sémantiques suivante s'appliquent à votre utilisation de l'argument `AS COPY OF` :  
  
-   Le nom du serveur source et le nom du serveur pour la cible de copie peuvent être identiques ou différents. Lorsqu’ils sont identiques, ce paramètre est facultatif et le contexte de serveur de la session active est utilisé par défaut.  
  
-   Les noms des bases de données source et de destination doivent être spécifiées, uniques et conformes aux règles applicables aux identificateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [identificateurs](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
-   L'instruction `CREATE DATABASE` doit être exécutée dans le contexte de la base de données master du serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] où la nouvelle base de données sera créée.  
  
-   Une fois la copie terminée, la base de données de destination doit être gérée comme une base de données indépendante. Vous pouvez exécuter les instructions `ALTER DATABASE` et `DROP DATABASE` contre la nouvelle base de données indépendamment de la base de données source. Vous pouvez également copier la nouvelle base de données vers une autre nouvelle base de données.  
  
-   La base de données source est toujours accessible pendant que la copie de base de données est en cours.  
  
 Pour plus d’informations, consultez [créer une copie d’une base de données SQL Azure à l’aide de Transact-SQL](https://azure.microsoft.com/documentation/articles/sql-database-copy-transact-sql/).  
  
## <a name="permissions"></a>Autorisations  
 Pour créer une base de données à un compte de connexion doit être une des opérations suivantes :  
  
-   La connexion du principal au niveau du serveur  
  
-   L’administrateur Azure AD pour Azure SQL Server local  
  
-   Une connexion qui est un membre de la `dbmanager` rôle de base de données  
  
 **Exigences supplémentaires pour l’utilisation de `CREATE DATABASE ... AS COPY OF` syntaxe :** la connexion exécutant l’instruction sur le serveur local doit également être au moins égale au `db_owner` sur le serveur source. Si la connexion est basée sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, la connexion exécutant l’instruction sur le serveur local doit avoir une connexion correspondante sur la source de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] server, avec les mêmes nom et mot de passe.  
  
## <a name="examples"></a>Exemples  
Pour obtenir un didacticiel de démarrage rapide vous montrant comment se connecter à une base de données SQL Azure à l’aide de SQL Server Management Studio, consultez [base de données SQL Azure : utilisation de SQL Server Management Studio pour vous connecter et interroger des données](/azure/sql-database/sql-database-connect-query-ssms).  
  
### <a name="simple-example"></a>Exemple simple  
 Un exemple simple pour la création d’une base de données.  
  
```sql  
CREATE DATABASE TestDB1;  
```  
  
### <a name="simple-example-with-edition"></a>Exemple simple avec l’édition  
 Un exemple simple pour la création d’une base de données standard.  
  
```sql  
CREATE DATABASE TestDB2  
( EDITION = 'standard' );  
```  
  
### <a name="example-with-additional-options"></a>Exemple avec des Options supplémentaires  
 Un exemple d’utilisation de plusieurs options.  
  
```sql  
CREATE DATABASE hito   
COLLATE Japanese_Bushu_Kakusu_100_CS_AS_KS_WS   
( MAXSIZE = 500 MB, EDITION = 'standard', SERVICE_OBJECTIVE = 'S1' ) ;  
```  
  
### <a name="creating-a-copy"></a>Création d’une copie  
 Un exemple de création d’une copie d’une base de données.  
  
```sql  
CREATE DATABASE escuela   
AS COPY OF school;  
```  
  
### <a name="creating-a-database-in-an-elastic-pool"></a>Création d’une base de données dans un Pool élastique  
 Crée la base de données dans le pool nommé S3M100 :  
  
```sql  
CREATE DATABASE db1 ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = S3M100 ) ) ;  
```  
  
### <a name="creating-a-copy-of-a-database-on-another-server"></a>Création d’une copie d’une base de données sur un autre serveur  
 L’exemple suivant crée une copie de la base de données db_original, nommé db_copy dans le niveau de performance P2 pour une base de données.  Cela est vrai que db_original soit dans un pool élastique ou d’un niveau de performance pour une base de données.  
  
```sql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original ( SERVICE_OBJECTIVE = 'P2' )  ;  
```  
  
 L’exemple suivant crée une copie de la base de données db_original, nommé db_copy dans un pool élastique nommé ep1.  Cela est vrai que db_original soit dans un pool élastique ou d’un niveau de performance pour une base de données.  Si db_original se trouve dans un pool élastique avec un nom différent, puis db_copy est toujours créé dans ep1.  
  
```sql  
CREATE DATABASE db_copy   
    AS COPY OF ozabzw7545.db_original   
    (SERVICE_OBJECTIVE = ELASTIC_POOL( name = ep1 ) ) ;  
```  

### <a name="create-database-with-specified-catalog-collation-value"></a>Créer la base de données avec la valeur de classement de catalogue spécifié

L’exemple suivant définit le classement de catalogue pour DATABASE_DEFAULT lors de la création de base de données, qui définit le classement de catalogue pour être le même que le classement de base de données.

```sql
CREATE DATABASE TestDB3 COLLATE Japanese_XJIS_140  (MAXSIZE = 100 MB, EDITION = ‘basic’)  
      WITH CATALOG_COLLATION = DATABASE_DEFAULT 
```
  
## <a name="see-also"></a>Voir aussi  

-  [Sys.dm_database_copies &#40; Base de données SQL Azure &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)

-   [ALTER DATABASE &#40; Base de données SQL Azure &#41;](alter-database-azure-sql-database.md)   
    
  

