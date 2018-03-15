---
title: "_ (Caractère générique - Recherche d’un seul caractère) (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
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
dev_langs:
- TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- _ (wildcard - match one character)
ms.assetid: 11a2ed36-9e21-4bdf-ae20-a31db1434b97
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 01bc0c4c006ae55395d752a0377575fa680dffaa
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="-wildcard---match-one-character-transact-sql"></a>_ (Caractère générique - recherche de correspondance d'un seul caractère) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Utilisez le trait de soulignement _ pour recherche un caractère unique dans une opération de comparaison de chaînes qui inclut des critères spéciaux, comme `LIKE` et `PATINDEX`.  
  
## <a name="examples"></a>Exemples  

## <a name="a-simple-example"></a>A. Exemple simple   

L’exemple suivant retourne tous les noms de base de données qui commencent par la lettre `m` et dont la troisième lettre est `d`. Le caractère de soulignement indique que le deuxième caractère du nom peut être n’importe quelle lettre. Les bases de données `model` et `msdb` répondent à ces critères. La base de données `master` n’y répond pas.

```sql
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
Vous pouvez avoir d’autres bases de données qui répondent à ces critères.

Vous pouvez utiliser plusieurs traits de soulignement pour représenter plusieurs caractères. Si vous modifiez les critères `LIKE` de sorte à inclure deux traits de soulignement `'m__%`, alors la base de données MASTER est incluse dans les résultats.

### <a name="b-more-complex-example"></a>B. Exemple plus complexe
 Cet exemple utilise l’opérateur _ pour rechercher toutes les personnes figurant dans la table `Person` qui ont un prénom en trois lettres se terminant par `an`.  
  
```sql  
-- USE AdventureWorks2012
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE '_an'  
ORDER BY FirstName;  
```  
## <a name="c-escaping-the-underscore-character"></a>C. Échappement du caractère de soulignement   
L’exemple suivant retourne les noms des rôles de base de données fixes comme `db_owner` et `db_ddladmin`, mais elle retourne également l’utilisateur `dbo`. 

```sql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db_%';
```

Le trait de soulignement en troisième position de caractère est considéré comme un caractère générique et ne permet pas de filtrer seulement les principaux qui commencent par les lettres `db_`. Pour échapper le trait de soulignement, placez-le entre crochets `[_]`. 

```sql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db[_]%';
```   
Maintenant, l’utilisateur `dbo` est exclu.   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
```
name
-------------
db_owner
db_accessadmin
db_securityadmin
...
```

  
## <a name="see-also"></a> Voir aussi  
 [LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)   
  [% (Caractère générique - Caractères à rechercher)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [&#91; &#93; (Caractère générique - Caractères à rechercher)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [&#91;^&#93; (Caractère générique - Caractères à exclure)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
  
