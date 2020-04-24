---
title: DROP EXTERNAL TABLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 02a6a236-0756-4570-abfa-6f677a7df042
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 75358e74102b958a8512ea20a1f75a36d735cb9a
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632829"
---
# <a name="drop-external-table-transact-sql"></a>DROP EXTERNAL TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Supprime une table externe PolyBase d’une base de données, mais pas les données externes.  
  
 ![Icône Lien d’article](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien d’article") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
DROP EXTERNAL TABLE { database_name.schema_name.table_name | schema_name.table_name | table_name }
[;]  
```  
  

## <a name="arguments"></a>Arguments  
 `[ database_name . [schema_name] . | schema_name . ] table_name`  
 Nom (composé d’une à trois parties) de la table externe à supprimer. Si vous le souhaitez, le nom de table peut inclure le schéma, ou la base de données et le schéma.  
  
## <a name="permissions"></a>Autorisations  
  
-   Nécessite une autorisation **ALTER** pour le schéma auquel appartient la table.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 La suppression d’une table externe supprime toutes les métadonnées relatives à cette table. Cela ne supprime pas les données externes.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-basic-syntax"></a>R. Utilisation de la syntaxe de base  
  
```  
DROP EXTERNAL TABLE SalesPerson;  
DROP EXTERNAL TABLE dbo.SalesPerson;  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
### <a name="b-dropping-an-external-table-from-the-current-database"></a>B. Suppression d’une table externe dans la base de données active  
 Cet exemple supprime la table `ProductVendor1`, ainsi que ses données, ses index et toutes les vues dépendantes de la base de données active.  
  
```  
DROP EXTERNAL TABLE ProductVendor1;  
```  
  
### <a name="c-dropping-a-table-from-another-database"></a>C. Suppression d’une table dans une autre base de données  
 L'exemple suivant supprime la table `SalesPerson` de la base de données `EasternDivision`.  
  
```  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
