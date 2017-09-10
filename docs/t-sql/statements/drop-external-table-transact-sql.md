---
title: DROP TABLE externe (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 02a6a236-0756-4570-abfa-6f677a7df042
caps.latest.revision: 12
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0e560c5341abd440f641a988751a6ca2875b9bbb
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-external-table-transact-sql"></a>DROP TABLE externe (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Supprime une table externe PolyBase à partir de. Cela ne supprime pas les données externes.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DROP EXTERNAL TABLE [ database_name . [schema_name ] . | schema_name . ] table_name   
[;]  
```  
  

## <a name="arguments"></a>Arguments  
 [ *nom_base_de_données* . [*schema_name*]. | *schema_name* . ] *nom_table*  
 Le nom d’une à trois parties de la table externe à supprimer. Le nom de table peut éventuellement inclure le schéma, ou la base de données et le schéma.  
  
## <a name="permissions"></a>Permissions  
  
-   Requiert **ALTER** autorisation sur le schéma auquel appartient la table.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Suppression d’une table externe supprime toutes les métadonnées de table. Elle ne supprime pas les données externes.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-basic-syntax"></a>A. À l’aide de la syntaxe de base  
  
```  
DROP EXTERNAL TABLE SalesPerson;  
DROP EXTERNAL TABLE dbo.SalesPerson;  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
### <a name="b-dropping-an-external-table-from-the-current-database"></a>B. Suppression d’une table externe à partir de la base de données en cours  
 L’exemple suivant supprime le `ProductVendor1` table, ses données, index et toutes les vues dépendantes à partir de la base de données actuelle.  
  
```  
DROP EXTERNAL TABLE ProductVendor1;  
```  
  
### <a name="c-dropping-a-table-from-another-database"></a>C. Suppression d’une table à partir d’une autre base de données  
 L'exemple suivant supprime la table `SalesPerson` de la base de données `EasternDivision`.  
  
```  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-basic-syntax"></a>D. À l’aide de la syntaxe de base  
  
```  
DROP EXTERNAL TABLE SalesPerson;  
DROP EXTERNAL TABLE dbo.SalesPerson;  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
### <a name="e-dropping-an-external-table-from-the-current-database"></a>E. Suppression d’une table externe à partir de la base de données en cours  
 L’exemple suivant supprime le `ProductVendor1` table, ses données, index et toutes les vues dépendantes à partir de la base de données actuelle.  
  
```  
DROP EXTERNAL TABLE ProductVendor1;  
```  
  
### <a name="f-dropping-a-table-from-another-database"></a>F. Suppression d’une table à partir d’une autre base de données  
 L'exemple suivant supprime la table `SalesPerson` de la base de données `EasternDivision`.  
  
```  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  


