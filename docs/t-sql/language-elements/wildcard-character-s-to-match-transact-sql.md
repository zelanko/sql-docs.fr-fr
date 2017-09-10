---
title: "(Caractère générique - caractères à comparer) (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Match
- wildcard
- '[ ]'
- '[_]_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[ ] (wildcard - character(s) to match)'
ms.assetid: 57817576-0bf1-49ed-b05d-fac27e8fed7a
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 18688c96cd0369905844d79a1a109f4e5032bce3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="wildcard---characters-to-match-transact-sql"></a>(Caractère générique - caractères à comparer) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Correspond à n’importe quel caractère unique dans la plage spécifiée ou l’ensemble spécifié entre crochets `[ ]`. Ces caractères génériques peuvent être utilisés dans les comparaisons de chaînes qui impliquent des critères spéciaux, tels que `LIKE` et `PATINDEX`.  
  
## <a name="examples"></a>Exemples  
### <a name="a-simple-example"></a>R : exemple simple de   
L’exemple suivant retourne les noms des qui commencent par la lettre `m`. `[n-z]`Spécifie que la deuxième lettre doit être quelque part dans la plage comprise entre `n` à `z`. Le caractère générique de pourcentage `%` permet à tout ou aucun des caractères en commençant par le caractère de 3. Le `model` et `msdb` bases de données répondent à ces critères. Le `master` n’est pas de base de données et est exclu du jeu de résultats.
 
```tsql
SELECT name FROM sys.databases
WHERE name LIKE 'm[n-z]%';
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]  

```
name
-----
model
msdb
```   
 Vous pouvez avoir des bases de données qualifiants supplémentaires installées.


### <a name="b-more-complex-example"></a>B : exemple plus complexe.   
 L'exemple suivant utilise l'opérateur [] pour rechercher l'ID et le nom de tous les employés de [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] dont le code postal se compose de quatre chiffres.  
  
```tsql  
-- Uses AdventureWorks  
  
SELECT e.BusinessEntityID, p.FirstName, p.LastName, a.PostalCode  
FROM HumanResources.Employee AS e  
INNER JOIN Person.Person AS p ON e.BusinessEntityID = p.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS ea ON e.BusinessEntityID = ea.BusinessEntityID  
INNER JOIN Person.Address AS a ON a.AddressID = ea.AddressID  
WHERE a.PostalCode LIKE '[0-9][0-9][0-9][0-9]';  
```  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
EmployeeID      FirstName      LastName      PostalCode  
----------      ---------      ---------     ----------  
290             Lynn           Tsoflias      3000  
```  



  
## <a name="see-also"></a>Voir aussi  
 [COMME &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [La fonction PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
  [% (Caractère générique - caractères à comparer)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
 [&#91; ^ &#93; (Caractère générique - caractères à ne pas faire correspondre)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
 [_ (Caractère générique - représente un caractère)](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
    
  

