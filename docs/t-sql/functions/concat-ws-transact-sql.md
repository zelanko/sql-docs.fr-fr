---
title: CONCAT_WS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 377db445118e55f1bdeec220f1e6701e9f89706c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="concatws-transact-sql"></a>CONCAT_WS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

Concatène un nombre variable d’arguments avec un délimiteur spécifié dans l’argument 1er. (`CONCAT_WS` indique *concatène avec séparateur*.)

##  <a name="syntax"></a>Syntaxe   
```sql
CONCAT_WS ( separator, argument1, argument1 [, argumentN]… ) 
```

## <a name="arguments"></a>Arguments   
séparateur  
Est une expression de n’importe quel type de caractère (`nvarchar`, `varchar`, `nchar`, ou `char`).

argument1, argument2, argument*N*  
Est une expression de n’importe quel type.

## <a name="return-types"></a>Types de retour
Chaîne. La longueur et le type dépendent de l’entrée.

## <a name="remarks"></a>Notes   
`CONCAT_WS`accepte un nombre variable d’arguments et les concatène en une seule chaîne à l’aide du premier argument comme séparateur. Il requiert un séparateur et un minimum de deux arguments ; Sinon, une erreur est générée. Tous les arguments sont implicitement convertis en types de chaîne et sont ensuite concaténées. 

La conversion implicite en chaînes respecte les règles existantes de conversion de type de données. Pour plus d’informations sur les conversions de type de comportement et les données, consultez [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md).

### <a name="treatment-of-null-values"></a>Traitement des valeurs NULL

`CONCAT_WS`ignore le `SET CONCAT_NULL_YIELDS_NULL {ON|OFF}` paramètre.

Si tous les arguments sont null, une chaîne vide de type `varchar(1)` est retourné. 

Les valeurs NULL sont ignorés lors de la concaténation et n’ajoute pas le séparateur. Cela facilite le scénario courant de la concaténation de chaînes qui contiennent souvent des valeurs vides, tel qu’un deuxième champ d’adresse. Consultez l’exemple B.

Si votre scénario requiert des valeurs null pour être inclus dans un séparateur, reportez-vous à l’aide de l’exemple C le `ISNULL` (fonction).

## <a name="examples"></a>Exemples   

### <a name="a--concatenating-values-with-separator"></a>A.  Concaténer des valeurs avec séparateur
L’exemple suivant concatène trois colonnes de la table sys.databases, en séparant les valeurs avec un `- `.   

```sql
SELECT CONCAT_WS( ' - ', database_id, recovery_model_desc, containment_desc) AS DatabaseInfo
FROM sys.databases;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

|DatabaseInfo |  
|---------|
|1 - SIMPLE - AUCUN |
|2 - SIMPLE - AUCUN |
|3 - FULL - AUCUN |
|4 - SIMPLE - AUCUN |


### <a name="b--skipping-null-values"></a>B.  Ignorer les valeurs NULL
L’exemple suivant ignore `NULL` valeurs dans la liste d’arguments.

```sql
SELECT CONCAT_WS(',','1 Microsoft Way', NULL, NULL, 'Redmond', 'WA', 98052) AS Address;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
Address
------------   
1 Microsoft Way,Redmond,WA,98052
```

### <a name="c--generating-csv-file-from-table"></a>C.  Génération du fichier CSV à partir de la table
L’exemple suivant utilise une virgule comme séparateur et ajoute le caractère de retour chariot pour entraîner le format de valeurs séparées par des valeurs de colonne.

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

CONCAT_WS ignore les valeurs NULL dans les colonnes. Si certaines colonnes sont nullables, placez-le avec `ISNULL` la fonction et fournir la valeur par défaut, comme dans l’exemple suivant :

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, ISNULL(recovery_model_desc,''), ISNULL(containment_desc,'N/A')), char(13)) AS DatabaseInfo
FROM sys.databases;
```

## <a name="see-also"></a>Voir aussi
[Fonctions de chaîne (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
[CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md)      


