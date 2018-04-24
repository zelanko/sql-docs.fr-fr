---
title: CONCAT_WS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CONCAT_WS
- CONCAT_WS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT_WS function
ms.assetid: f1375fd7-a2fd-48bf-922a-4f778f0deb1f
caps.latest.revision: 5
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 171d063e746393709629720dae40eb207d45d584
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="concatws-transact-sql"></a>CONCAT_WS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Concatène un nombre variable d’arguments avec un délimiteur spécifié dans le 1er argument. (`CONCAT_WS` indique *concaténer avec un séparateur*.)

##  <a name="syntax"></a>Syntaxe   
```sql
CONCAT_WS ( separator, argument1, argument1 [, argumentN]… ) 
```

## <a name="arguments"></a>Arguments   
separator  
Expression de tout type de caractère (`nvarchar`, `varchar`, `nchar` ou `char`).

argument1, argument2, argument*N*  
Expression de tout type.

## <a name="return-types"></a>Types de retour
Chaîne. La longueur et le type dépendent de l’entrée.

## <a name="remarks"></a>Notes    
`CONCAT_WS` prend un nombre variable d’arguments et les concatène en une chaîne unique en utilisant le premier argument comme séparateur. La fonction nécessite un séparateur et un minimum de deux arguments ; sinon, une erreur est générée. Tous les arguments sont implicitement convertis en types chaîne et ensuite concaténés. 

La conversion implicite en chaînes respecte les règles existantes de conversion de type de données. Pour plus d’informations sur le comportement et les conversions de type de données, consultez [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md).

### <a name="treatment-of-null-values"></a>Traitement des valeurs NULL

`CONCAT_WS` ignore le paramètre `SET CONCAT_NULL_YIELDS_NULL {ON|OFF}`.

Si tous les arguments sont NULL, une chaîne vide de type `varchar(1)` est renvoyée. 

Les valeurs NULL sont ignorées durant la concaténation et le séparateur n’est pas ajouté. Cela facilite le scénario courant de la concaténation de chaînes contenant souvent des valeurs vides, telles qu’un second champ d’adresse. Voir l’exemple B.

Si votre scénario requiert l’insertion de valeurs NULL à l’aide d’un séparateur, consultez l’exemple C sur l’utilisation de la fonction `ISNULL`.

## <a name="examples"></a>Exemples   

### <a name="a--concatenating-values-with-separator"></a>A.  Concaténer des valeurs avec séparateur
L’exemple suivant concatène trois colonnes de la table sys.databases, en séparant les valeurs par `- `.   

```sql
SELECT CONCAT_WS( ' - ', database_id, recovery_model_desc, containment_desc) AS DatabaseInfo
FROM sys.databases;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

|DatabaseInfo |  
|---------|
|1 - SIMPLE - NONE |
|2 - SIMPLE - NONE |
|3 - FULL - NONE |
|4 - SIMPLE - NONE |


### <a name="b--skipping-null-values"></a>B.  Ignorer les valeurs NULL
L’exemple suivant ignore les valeurs `NULL` dans la liste des arguments.

```sql
SELECT CONCAT_WS(',','1 Microsoft Way', NULL, NULL, 'Redmond', 'WA', 98052) AS Address;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
Address
------------   
1 Microsoft Way,Redmond,WA,98052
```

### <a name="c--generating-csv-file-from-table"></a>C.  Générer un fichier CSV à partir de la table
L’exemple suivant utilise une virgule comme séparateur et ajoute le caractère de retour chariot au résultat dans le format de valeurs séparées par des colonnes.

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, recovery_model_desc, containment_desc), char(13)) AS DatabaseInfo
FROM sys.databases
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
DatabaseInfo
------------   
1,SIMPLE,NONE
2,SIMPLE,NONE
3,FULL,NONE 
4,SIMPLE,NONE 
```

CONCAT_WS ignore les valeurs NULL dans les colonnes. Si certaines colonnes sont de type nullable, encapsulez-les avec la fonction `ISNULL` et fournissez la valeur par défaut, comme dans l’exemple suivant :

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, ISNULL(recovery_model_desc,''), ISNULL(containment_desc,'N/A')), char(13)) AS DatabaseInfo
FROM sys.databases;
```

## <a name="see-also"></a>Voir aussi
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  

