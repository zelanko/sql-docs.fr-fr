---
title: "_ (Caractère générique - représente un caractère) (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- Match
- wildcard
- _TSQL
- Match One
- _
dev_langs: TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- _ (wildcard - match one character)
ms.assetid: 11a2ed36-9e21-4bdf-ae20-a31db1434b97
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f6134bec732593480cd20973eb7687a29cfbf2b8
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="-wildcard---match-one-character-transact-sql"></a>_ (Caractère générique - recherche de correspondance d'un seul caractère) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Utilisez le caractère de soulignement _ pour correspondre à n’importe quel caractère unique dans une opération de comparaison de chaînes qui inclut des critères spéciaux, tels que `LIKE` et `PATINDEX`.  
  
## <a name="examples"></a>Exemples  

## <a name="a-simple-example"></a>R : exemple simple de   

L’exemple suivant retourne tous les noms qui commencent par la lettre de la base de données `m` et avoir la lettre `d` la troisième lettre. Le caractère de soulignement Spécifie que le deuxième caractère du nom peut être n’importe quelle lettre. Le `model` et `msdb` bases de données répondent à ces critères. Le `master` n’est pas le cas de base de données.

```tsql
SELECT name FROM sys.databases
WHERE name LIKE 'm_d%';
```   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
```
name
-----
model
msdb
```   
Vous pouvez avoir des bases de données supplémentaires qui répondent à ces critères.

Vous pouvez utiliser plusieurs traits de soulignement pour représenter plusieurs caractères. Modification de la `LIKE` critères pour inclure les deux traits de soulignement `'m__%` inclut la base de données master dans le résultat.

### <a name="b-more-complex-example"></a>B : exemple plus complexe.
 L’exemple suivant utilise l’opérateur _ pour rechercher tous les habitants de la `Person` table, qui ont un prénom de trois lettres se terminant par `an`.  
  
```tsql  
-- USE AdventureWorks2012
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE '_an'  
ORDER BY FirstName;  
```  
## <a name="c-escaping-the-underscore-character"></a>C: échappement le caractère de soulignement   
L’exemple suivant retourne les noms des rôles de base de données fixe comme `db_owner` et `db_ddladmin`, mais elle retourne également la `dbo` utilisateur. 

```tsql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db_%';
```

Le trait de soulignement en troisième position de caractère est considéré comme un caractère générique et n’est pas le filtrage pour seulement les entités en commençant par les lettres `db_`. Pour échapper le caractère de soulignement entre crochets `[_]`. 

```tsql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db[_]%';
```   
Maintenant le `dbo` utilisateur est exclu.   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
```
name
-------------
db_owner
db_accessadmin
db_securityadmin
...
```

  
## <a name="see-also"></a>Voir aussi  
 [COMME &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [La fonction PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
  [% (Caractère générique - caractères à comparer)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [&#91; &#93; (Caractère générique - caractères à comparer)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [&#91; ^ &#93; (Caractère générique - caractères à ne pas faire correspondre)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
  
