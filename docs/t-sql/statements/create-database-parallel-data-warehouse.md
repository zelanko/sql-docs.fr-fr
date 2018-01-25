---
title: "CRÉER la base de données (Parallel Data Warehouse) | Documents Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40cacde4-ac72-45f7-9564-d76e2b4a741a
caps.latest.revision: "13"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e9ff76a4d260604a93f59baa3b61f5c37b4952f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="create-database-parallel-data-warehouse"></a>CRÉER la base de données (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Crée une nouvelle base de données sur un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] appliance. Utilisez cette instruction pour créer tous les fichiers associés à une base de données et définir les options de croissance automatique pour les tables de base de données et le journal des transactions et de la taille maximale.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CREATE DATABASE database_name   
WITH (   
    [ AUTOGROW = ON | OFF , ]   
    REPLICATED_SIZE = replicated_size [ GB ] ,  
    DISTRIBUTED_SIZE = distributed_size [ GB ] ,  
    LOG_SIZE = log_size [ GB ] )  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Nom de la nouvelle base de données. Pour plus d’informations sur les noms de base de données autorisées, consultez « Règles d’affectation de noms d’objet » et « Noms réservés de base de données » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 CROISSANCE AUTOMATIQUE = ON | **OFF**  
 Spécifie si le *replicated_size*, *distributed_size*, et *log_size* paramètres pour cette base de données croît automatiquement en fonction des besoins au-delà de leur taille spécifiée. Valeur par défaut est **OFF**.  
  
 Si la croissance automatique est activée, *replicated_size*, *distributed_size*, et *log_size* augmentera comme requis (pas dans les blocs de la taille spécifiée initiale) avec chaque insertion de données, mise à jour, ou autre action qui nécessite davantage de stockage qu’a déjà été alloué.  
  
 Si la croissance automatique est désactivée, la taille n’augmente pas selon automatiquement. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]Retourne une erreur lors de la tentative d’une action qui nécessite *replicated_size*, *distributed_size*, ou *log_size* à croître au-delà de leur valeur spécifiée.  
  
 Croissance automatique est activé pour toutes les tailles ou OFF pour toutes les tailles. Par exemple, il n’est pas possible de définir de croissance automatique pour *log_size*, mais pas définie pour *replicated_size*.  
  
 *replicated_size* [ GB ]  
 Un nombre positif. Définit la taille (en gigaoctets entier ou décimal) pour l’espace total alloué pour les tables répliquées et les données correspondantes *sur chaque nœud de calcul*. Pour les valeurs minimale et maximale *replicated_size* configuration requise, consultez « Valeurs minimale et maximale » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Si la croissance automatique est activée, les tables répliquées seront autorisées à croître au-delà de cette limite.  
  
 Si la croissance automatique est désactivée, une erreur est renvoyée si un utilisateur tente de créer une table répliquée, insertion de données dans une réplication de table, ou mettre à jour un existant table répliquée dans une manière qui augmenterait la taille au-delà de *replicated_size*.  
  
 *distributed_size* [ GB ]  
 Un nombre positif. La taille, en gigaoctets entière ou décimale, pour l’espace total alloué aux tables distribuées (et aux données correspondantes) *sur l’appliance*. Pour les valeurs minimale et maximale *distributed_size* configuration requise, consultez « Valeurs minimale et maximale » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Si la croissance automatique est activée, les tables distribuées seront autorisées à croître au-delà de cette limite.  
  
 Si la croissance automatique est désactivée, une erreur est renvoyée si un utilisateur tente de créer une nouvelle table distribuée, insérer des données dans un distributed existant de table, ou mettre à jour une table distribuée existante d’une manière qui augmenterait la taille au-delà de *distributed_size*.  
  
 *log_size* [ GB ]  
 Un nombre positif. La taille (en gigaoctets entier ou décimal) pour le journal des transactions *sur l’appliance*.  
  
 Pour les valeurs minimale et maximale *log_size* configuration requise, consultez « Valeurs minimale et maximale » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Si la croissance automatique est activée, le fichier journal est autorisé à croître au-delà de cette limite. Utilisez le [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) instruction afin de réduire la taille des fichiers journaux à leur taille d’origine.  
  
 Si la croissance automatique est désactivée, une erreur s’affichera à l’utilisateur pour toute action qui augmenterait la taille du journal sur un nœud de calcul individuelles au-delà de *log_size*.  
  
## <a name="permissions"></a>Autorisations  
 Requiert le **CREATE ANY DATABASE** autorisation dans la base de données master, ou l’appartenance dans le **sysadmin** rôle serveur fixe.  
  
 L'exemple suivant fournit l'autorisation de créer une base de données à l'utilisateur de base de données Fay.  
  
```  
USE master;  
GO  
GRANT CREATE ANY DATABASE TO [Fay];  
GO  
```  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Bases de données sont créées avec le niveau de compatibilité de base de données 120, ce qui constitue la compatibilité au niveau de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Cela garantit que la base de données sera en mesure d’utiliser tous les [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] fonctionnalité PDW utilise.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 L’instruction CREATE DATABASE n’est pas autorisée dans une transaction explicite. Pour plus d’informations, consultez [instructions](../../t-sql/statements/statements.md).  
  
 Pour plus d’informations sur les contraintes de minimales et maximales des bases de données, consultez « Valeurs minimale et maximale » dans le [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Au moment de la création d’une base de données, il doit être suffisamment d’espace libre disponible *sur chaque nœud de calcul* pour allouer le total combiné des tailles suivantes :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]base de données avec des tables de la taille de *replicated_table_size*.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]base de données avec des tables de la taille de (*distributed_table_size* / nombre de nœuds de calcul).  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]enregistre la taille de (*log_size* / nombre de nœuds de calcul).  
  
## <a name="locking"></a>Verrouillage  
 Acquiert un verrou partagé sur l’objet de base de données.  
  
## <a name="metadata"></a>Métadonnées  
 Une fois cette opération réussit, une entrée pour cette base de données s’affiche dans le [sys.databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) et [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)des vues de métadonnées.  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Exemples :[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-basic-database-creation-examples"></a>A. Exemples de création de base de données  
 L’exemple suivant crée la base de données `mytest` avec une allocation de stockage de 100 Go par nœud de calcul pour les tables répliquées, 500 Go par appliance pour les tables distribuées et 100 Go par appliance pour le journal des transactions. Dans cet exemple, la croissance automatique est désactivée par défaut.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB );  
```  
  
 L’exemple suivant crée la base de données `mytest` avec les mêmes paramètres que celles mentionnées ci-dessus, à l’exception de croissance automatique est activée. Cela permet d’augmenter les paramètres de la taille spécifiée à l’extérieur de la base de données.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (AUTOGROW = ON,  
   REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB);  
```  
  
### <a name="b-creating-a-database-with-partial-gigabyte-sizes"></a>B. Création d’une base de données avec des tailles de gigaoctets partielle  
 L’exemple suivant crée la base de données `mytest`, avec la croissance automatique désactivé, une allocation de stockage de 1,5 Go par nœud de calcul pour les tables répliquées, 5,25 Go par appliance pour les tables distribuées et 10 Go par appliance pour le journal des transactions.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 1.5 GB,  
   DISTRIBUTED_SIZE = 5.25 GB,  
   LOG_SIZE = 10 GB);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40; Parallel Data Warehouse &#41;](../../t-sql/statements/alter-database-parallel-data-warehouse.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
