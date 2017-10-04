---
title: "CRÉER la base de données (entrepôt de données SQL Azure) | Documents Microsoft"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 03/14/2017
ms.prod: 
ms.reviewer: 
ms.service: sql-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 42819b93-b757-4b2c-8179-d4be3c512c19
caps.latest.revision: 20
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a178756610f0d0e463c21a2a62a287ada6c863a1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-database-azure-sql-data-warehouse"></a>CRÉER la base de données (entrepôt de données SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Crée une base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CREATE DATABASE database_name [ COLLATE collation_name ]  
(  
    [ MAXSIZE = { 250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 | 92160 | 102400 | 153600 | 204800 | 245760 } GB ,]  
    EDITION = 'datawarehouse',  
    SERVICE_OBJECTIVE = { 'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' | 'DW3000' | 'DW6000' }  
)  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
*database_name*  
Nom de la nouvelle base de données. Ce nom doit être unique sur le serveur SQL, qui peut héberger à la fois [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] bases de données et [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] des bases de données et doit respecter le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] règles applicables aux identificateurs. Pour plus d’informations, consultez [identificateurs](http://go.microsoft.com/fwlink/p/?LinkId=180386).  
  
*collation_name*  
Indique le classement par défaut de la base de données. Le nom du classement peut être un nom de classement Windows ou SQL. Si non spécifié, la base de données reçoit le classement par défaut, qui est SQL_Latin1_General_CP1_CI_AS.  
  
Pour plus d’informations sur les noms de classements Windows et SQL, consultez [COLLATE (Transact-SQL)](http://msdn.microsoft.com/library/ms184391.aspx).  
  
*ÉDITION*  
Spécifie la couche de service de la base de données. Pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] utiliser « entrepôt de données ».  
  
*MAXSIZE*  
La taille maximale que peut atteindre la base de données. La définition de cette valeur empêche la croissance de la taille de la base de données au-delà de la taille définie. La valeur par défaut *MAXSIZE* lorsque ne pas spécifié est 10240 Go (10 To).  D’autres valeurs possibles allant jusqu'à 250 Go to 240.  
  
SERVICE_OBJECTIVE  
Spécifie le niveau de performances. Pour plus d’informations sur les objectifs de service pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], consultez [mise à l’échelle des performances sur SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-performance-scale/).  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
Utilisez [DATABASEPROPERTYEX &#40; Transact-SQL &#41; ](../../t-sql/functions/databasepropertyex-transact-sql.md) pour afficher les propriétés de la base de données.  
  
Utilisez [ALTER DATABASE &#40; Entrepôt de données SQL Azure &#41; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md) pour modifier la taille maximale, ou les valeurs d’objectif de service ultérieurement.   

Entrepôt de données SQL est défini sur COMPATIBILITY_LEVEL 130 et ne peut pas être modifié. Pour plus d’informations, consultez [amélioré les performances de requête avec 130 de niveau de compatibilité de base de données SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).
  
## <a name="permissions"></a>Permissions  
Autorisations requises :  
  
-   Connexion principale au niveau serveur, créée par le processus de déploiement, ou  
  
-   Membre de la `dbmanager` rôle de base de données.  
  
## <a name="error-handling"></a>Gestion des erreurs  
Si la taille de la base de données atteint la valeur MAXSIZE, vous recevez le code d’erreur 40544. Lorsque cela se produit, vous ne peut pas insérer et mettre à jour des données ou créer de nouveaux objets (tels que des tables, des procédures stockées, vues et fonctions). Vous pouvez toujours lire et supprimer des données, tronquer des tables, supprimer des tables et des index et reconstruire des index. Vous pouvez ensuite mettre à jour MAXSIZE avec une valeur supérieure à votre taille de base de données actuelle ou supprimer certaines données afin de libérer de l'espace de stockage. Vous devrez peut-être patienter jusqu'à quinze minutes avant de pouvoir insérer de nouvelles données.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
Vous devez être connecté à la base de données master pour créer une base de données.  
  
L'instruction `CREATE DATABASE` doit être la seule instruction dans un lot [!INCLUDE[tsql](../../includes/tsql-md.md)].

Vous ne pouvez pas modifier le classement de base de données après la création de la base de données.   
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd"></a>Exemples :[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
  
### <a name="a-simple-example"></a>A. Exemple simple  
Un exemple simple pour la création d’une base de données de l’entrepôt de données. Cela crée la base de données avec la plus petite taille max 10240 Go, le classement par défaut qui est SQL_Latin1_General_CP1_CI_AS et la puissance de calcul plus petite qui est DW100.  
  
```  
CREATE DATABASE TestDW  
(EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');  
```  
  
### <a name="b-create-a-data-warehouse-database-with-all-the-options"></a>B. Créer une base de données de l’entrepôt de données avec toutes les options  
Un exemple de création d’un entrepôt de données de 10 téraoctets à l’aide de toutes les options.  
  
```  
CREATE DATABASE TestDW COLLATE Latin1_General_100_CI_AS_KS_WS  
(MAXSIZE = 10240 GB, EDITION = 'datawarehouse', SERVICE_OBJECTIVE = 'DW1000');  
```  
  
## <a name="see-also"></a>Voir aussi  
[ALTER DATABASE &#40; Entrepôt de données SQL Azure &#40; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md) 
 [CREATE TABLE &#40; Entrepôt de données SQL Azure &#41; ](../../t-sql/statements/create-table-azure-sql-data-warehouse.md)  
 [Supprimer la base de données &#40; Transact-SQL &#40;](../../t-sql/statements/drop-database-transact-sql.md) 
  


