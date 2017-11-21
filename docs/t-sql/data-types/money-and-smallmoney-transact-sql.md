---
title: Money et smallmoney (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- money_TSQL
- money
- smallmoney
- smallmoney_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- money data type, about money data type
- money data type
- smallmoney data type
- values [SQL Server], monetary
- currency [SQL Server]
ms.assetid: 57861137-89ea-4b89-b361-390597d7bccc
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bd07ecd1cdacc686e0f831320fd5e939c0c174da
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="money-and-smallmoney-transact-sql"></a>money et smallmoney (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Types de données représentant des valeurs monétaires ou des devises.
  
## <a name="remarks"></a>Notes  
  
|Type de données|Plage|Stockage|  
|---|---|---|
|**money**|-922,337,203,685,477.5808 à 922,337,203,685,477.5807 (-922,337,203,685,477.58<br />pour 922,337,203,685,477.58 pour Informatica.  Informatica prend uniquement en charge deux décimales, quatre pas.)|8 octets|  
|**smallmoney**|-214 748,3648 à 214 748,3647|4 octets|  
  
Le **money** et **smallmoney** types de données sont précis à un dix millième près des unités monétaires qu’ils représentent. Pour Informatica, le **money** et **smallmoney** types de données sont précis à un centième des unités monétaires qu’ils représentent.
  
Utilisez un point pour séparer les unités monétaires partielles, comme les centimes, des unités monétaires entières. Par exemple, 2.15 signifie 2 dollars et 15 cents.
  
Ces types de données peuvent utiliser n'importe lequel des symboles monétaires suivants.
  
![Table de symboles monétaires, valeurs hexadécimales](../../t-sql/data-types/media/money01.gif "Table de symboles monétaires, valeurs hexadécimales")
  
Les valeurs de devise ou les données monétaires ne doivent pas être mises entre guillemets simples ('). Il est important de garder en mémoire que bien que vous puissiez spécifier des valeurs monétaires précédées d'un symbole de devise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne stocke pas les informations de devise associées au symbole, mais uniquement la valeur numérique.
  
## <a name="converting-money-data"></a>Conversion de données money
Lorsque vous convertissez **money** à partir de types de données integer, les unités sont supposées pour être des unités monétaires. Par exemple, la valeur entière 4 est convertie vers le **money** équivalent de 4 unités monétaires.
  
L’exemple suivant convertit **smallmoney** et **money** valeurs **varchar** et **décimal** types de données, respectivement.
  
```sql
DECLARE @mymoney_sm smallmoney = 3148.29,  
        @mymoney    money = 3148.29;  
SELECT  CAST(@mymoney_sm AS varchar) AS 'SM_MONEY varchar',  
        CAST(@mymoney AS decimal)    AS 'MONEY DECIMAL';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
SM_MONEY VARCHAR               MONEY DECIMAL  
------------------------------ ----------------------  
3148.29                        3148    
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md) 
 [CAST et CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md) 
 [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md) 
 [Des Types de données &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-types-transact-sql.md) 
 [DECLARE @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/declare-local-variable-transact-sql.md) 
 [Définir @local_variable &#40; Transact-SQL &#41; ](../../t-sql/language-elements/set-local-variable-transact-sql.md) 
 [sys.types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  

