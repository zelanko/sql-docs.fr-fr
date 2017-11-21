---
title: IDENTITY (fonction) (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IDENTITY_TSQL
- IDENTITY
dev_langs:
- TSQL
helpviewer_keywords:
- IDENTITY function
- SELECT statement [SQL Server], IDENTITY function
- inserting identity columns
- columns [SQL Server], creating
- identity columns [SQL Server], IDENTITY function
ms.assetid: ebec77eb-fc02-4feb-b6c5-f0098d43ccb6
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 43d42425842def7572cf7961a89cae355e6b78ae
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="identity-function-transact-sql"></a>IDENTITY (Fonction) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Est utilisé uniquement dans une instruction SELECT avec une INTO *table* clause pour insérer une colonne d’identité dans une nouvelle table. Bien qu'elles soient similaires, la fonction IDENTITY n'est pas identique à la propriété IDENTITY qui est utilisée avec CREATE TABLE et ALTER TABLE.  
  
> [!NOTE]  
>  Pour créer un numéro à incrémentation automatique qui peut être utilisé dans plusieurs tables ou être appelé par des applications sans faire référence à une table, consultez [Numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IDENTITY (data_type [ , seed , increment ] ) AS column_name  
```  
  
## <a name="arguments"></a>Arguments  
 *data_type*  
 Type de données de la colonne d'identité. Types de données valides pour une colonne d’identité sont des types de données de la catégorie de type de données entier, à l’exception de la **bits** type de données, ou **décimal** type de données.  
  
 *valeur initiale*  
 Entier à affecter à la première ligne de la table. Chaque ligne suivante est affectée à la valeur d’identité suivante, qui est égale à la dernière valeur IDENTITY plus la *incrément* valeur. Si ni *seed* ni *incrément* est spécifié, par défaut la valeur 1.  
  
 *incrément*  
 Valeur entière à ajouter à la *seed* valeur pour les lignes de la table.  
  
 *nom_colonne*  
 Nom de la colonne qui doit être insérée dans la nouvelle table.  
  
## <a name="return-types"></a>Types de retour  
 Retourne le même que *data_type*.  
  
## <a name="remarks"></a>Notes  
 Étant donné que cette fonction crée une colonne dans une table, vous devez spécifier pour la colonne un nom figurant dans la liste de sélection de l'une des manières suivantes :  
  
```  
--(1)  
SELECT IDENTITY(int, 1,1) AS ID_Num  
INTO NewTable  
FROM OldTable;  
  
--(2)  
SELECT ID_Num = IDENTITY(int, 1, 1)  
INTO NewTable  
FROM OldTable;  
  
```  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant insère toutes les lignes de la table `Contact` de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] dans une nouvelle table appelée `NewContact`. La fonction IDENTITY est utilisée pour démarrer les numéros d'identification à 100 au lieu de 1 dans la table `NewContact`.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'Person.NewContact', N'U') IS NOT NULL  
    DROP TABLE Person.NewContact;  
GO  
ALTER DATABASE AdventureWorks2012 SET RECOVERY BULK_LOGGED;  
GO  
SELECT  IDENTITY(smallint, 100, 1) AS ContactNum,  
        FirstName AS First,  
        LastName AS Last  
INTO Person.NewContact  
FROM Person.Person;  
GO  
ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
GO  
SELECT ContactNum, First, Last FROM Person.NewContact;  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [@@IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/identity-transact-sql.md)   
 [IDENTITY, propriété &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)   
 [Sélectionnez @local_variable &#40; Transact-SQL &#41;](../../t-sql/language-elements/select-local-variable-transact-sql.md)   
 [DBCC CHECKIDENT &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)   
 [Sys.identity_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-identity-columns-transact-sql.md)  
  
  

