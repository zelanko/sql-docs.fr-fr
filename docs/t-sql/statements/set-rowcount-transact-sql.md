---
title: SET ROWCOUNT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_ROWCOUNT_TSQL
- ROWCOUNT_TSQL
- SET ROWCOUNT
- ROWCOUNT
dev_langs:
- TSQL
helpviewer_keywords:
- row return limitations [SQL Server]
- SET ROWCOUNT statement
- number of rows affected by statement
- ROWCOUNT option
- counting rows
- stopping queries
- limiting rows returned
- queries [SQL Server], stopping
ms.assetid: c6966fb7-6421-47ef-98f3-82351f2f6bdc
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eda7f9faf2bb45b06cf1112dbe48cbdb281fdab3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-rowcount-transact-sql"></a>SET ROWCOUNT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Demande à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'arrêter l'exécution de la requête après avoir renvoyé le nombre de lignes spécifié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
SET ROWCOUNT { number | @number_var }   
```  
  
## <a name="arguments"></a>Arguments  
 *nombre* | @*var_nombre*  
 Nombre (entier) de lignes à traiter avant l'arrêt de la requête spécifiée.  
  
## <a name="remarks"></a>Notes  
  
> [!IMPORTANT]  
>  L'utilisation de SET ROWCOUNT n'affectera en rien les instructions DELETE, INSERT et UPDATE dans la version ultérieure de SQL Server. Évitez d’utiliser SET ROWCOUNT avec les instructions DELETE, INSERT et UPDATE dans tout nouveau développement et prévoyez de modifier les applications qui l’utilisent actuellement. Pour un comportement semblable, utilisez la syntaxe TOP. Pour plus d’informations, consultez [TOP &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
 Pour désactiver cette option de manière à renvoyer toutes les lignes, utilisez SET ROWCOUNT 0.  
  
 L'utilisation de l'option SET ROWCOUNT arrête le traitement de la plupart des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] lorsqu'elles ont atteint le nombre de lignes spécifié, Cela inclut les déclencheurs. L'option ROWCOUNT n'a aucun effet sur les curseurs dynamiques, mais elle limite l'ensemble de lignes de curseurs de type KEYSET et INSENSITIVE. Il convient d'être prudent lors de l'utilisation de cette option.  
  
 SET ROWCOUNT a priorité sur le mot clé TOP d'une instruction SELECT si le compte de lignes a la plus petite valeur.  
  
 L'option SET ROWCOUNT est définie lors de l'exécution, et non pas durant l'analyse.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle public.  
  
## <a name="examples"></a>Exemples  
 SET ROWCOUNT arrête le traitement après le nombre de lignes spécifié. Dans cet exemple, notez que plus de 500 lignes répondent aux critères de `Quantity` inférieure à `300`. Toutefois, après avoir appliqué SET ROWCOUNT, vous pouvez remarquer que toutes les lignes n'ont pas été retournées.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT count(*) AS Count  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Count`  
  
 `-----------`  
  
 `537`  
  
 `(1 row(s) affected)`  
  
 Définissez maintenant `ROWCOUNT` sur `4` et retournez toutes les lignes pour démontrer que seules 4 lignes sont retournées.  
  
```  
SET ROWCOUNT 4;  
SELECT *  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
```  
  
 `(4 row(s) affected)`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 SET ROWCOUNT arrête le traitement après le nombre de lignes spécifié. Dans l’exemple suivant, notez que plus de 20 lignes répondent aux critères de `AccountType = 'Assets'`. Toutefois, après avoir appliqué SET ROWCOUNT, vous pouvez remarquer que toutes les lignes n'ont pas été retournées.  
  
```  
-- Uses AdventureWorks  
  
SET ROWCOUNT 5;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
 Pour retourner toutes les lignes, set ROWCOUNT 0.  
  
```  
-- Uses AdventureWorks  
  
SET ROWCOUNT 0;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  


