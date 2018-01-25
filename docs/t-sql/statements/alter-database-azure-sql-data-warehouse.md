---
title: "ALTER DATABASE (entrepôt de données SQL Azure) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: da712a46-5f8a-4888-9d33-773e828ba845
caps.latest.revision: "20"
author: barbkess
ms.author: barbkess
manager: craigg
ms.openlocfilehash: 71737beb817cfeebed195c90d056768aef678a3e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="alter-database-azure-sql-data-warehouse"></a>MODIFIER la base de données (entrepôt de données SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Modifie le nom, une taille maximale ou un objectif de service pour une base de données.  
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ALTER DATABASE database_name  

  MODIFY NAME = new_database_name  
| MODIFY ( <edition_option> [, ... n] )  
  
<edition_option> ::=   
      MAXSIZE = { 
            250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 
          | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 
          | 92160 | 102400 | 153600 | 204800 | 245760 
      } GB  
      | SERVICE_OBJECTIVE = { 
            'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' 
          | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' 
          | 'DW3000' | 'DW6000' | 'DW1000c' | 'DW1500c' | 'DW2000c' 
          | 'DW2500c' | 'DW3000c' | 'DW5000c' | 'DW6000c' | 'DW7500c' 
          | 'DW10000c' | 'DW15000c' | 'DW30000c'
      }  
```  
  
## <a name="arguments"></a>Arguments  
*database_name*  
Spécifie le nom de la base de données à modifier.  

MODIFY NAME = *nouveau_nom_base_de_données*  
Renomme la base de données portant le nom spécifié en tant que *nouveau_nom_base_de_données*.  
  
MAXSIZE  
La valeur par défaut est 10 240 Go (10 To).  

**S’applique à :** optimisé pour le niveau de performance d’élasticité

La taille maximale autorisée pour la base de données. La base de données ne peut pas croître au-delà de MAXSIZE. 

**S’applique à :** optimisé pour le niveau de performances de calcul

La taille maximale autorisée pour les données rowstore dans la base de données. Les données stockées dans les tables rowstore, deltastore d’un index columnstore ou un index non cluster sur un index cluster columnstore ne peut pas croître au-delà de MAXSIZE.  Les données compressées au format columnstore n’ont pas d’une limite de taille et ne sont pas contraint par MAXSIZE. 
  
SERVICE_OBJECTIVE  
Spécifie le niveau de performances. Pour plus d’informations sur les objectifs de service pour [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)], consultez [des niveaux de performances](https://azure.microsoft.com/documentation/articles/performance-tiers/).  
  
## <a name="permissions"></a>Autorisations  
Ces autorisations sont nécessaires :  
  
-   Connexion du principal au niveau du serveur (celui créé par le processus de déploiement), ou  
  
-   Membre de la `dbmanager` rôle de base de données.  
  
Le propriétaire de la base de données ne peut pas modifier la base de données, sauf si le propriétaire est un membre de la `dbmanager` rôle.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
La base de données en cours doit être une base de données différent de celui que vous modifiez, par conséquent **ALTER doit être exécutée tout en étant connecté à la base de données master**.  
  
Entrepôt de données SQL est défini sur COMPATIBILITY_LEVEL 130 et ne peut pas être modifié. Pour plus d’informations, consultez [amélioré les performances de requête avec 130 de niveau de compatibilité de base de données SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).
  
Pour réduire la taille d’une base de données, utilisez [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
Pour exécuter l’instruction ALTER DATABASE, la base de données doit être en ligne et ne peut pas être dans un état suspendu.  
  
L’instruction ALTER DATABASE doit s’exécuter en mode de validation automatique, qui est le mode de gestion de transaction par défaut. Cela est défini dans les paramètres de connexion.  
  
L’instruction ALTER DATABASE ne peut pas faire partie d’une transaction définie par l’utilisateur.

Vous ne pouvez pas modifier le classement de base de données.  
  
## <a name="examples"></a>Exemples  
Avant d’exécuter ces exemples, assurez-vous que la base de données que vous modifiez n’est pas la base de données actuelle. La base de données en cours doit être une base de données différent de celui que vous modifiez, par conséquent **ALTER doit être exécutée tout en étant connecté à la base de données master**.  

### <a name="a-change-the-name-of-the-database"></a>A. Modifier le nom de la base de données  

```  
ALTER DATABASE AdventureWorks2012  
MODIFY NAME = Northwind;  
```  
  
### <a name="b-change-max-size-for-the-database"></a>B. Modifier la taille maximale de la base de données  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB );  
```  
  
### <a name="c-change-the-performance-level"></a>C. Modifier le niveau de performance  
  
```  
ALTER DATABASE dw1 MODIFY ( SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
### <a name="d-change-the-max-size-and-the-performance-level"></a>D. Modifier la taille maximale et le niveau de performance  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB, SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
## <a name="see-also"></a>Voir aussi  
[CRÉER une base de données (Azure SQL Data Warehouse)](../../t-sql/statements/create-database-azure-sql-data-warehouse.md)
[liste SQL Data Warehouse de rubriques de référence](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-overview-reference/)  
  
