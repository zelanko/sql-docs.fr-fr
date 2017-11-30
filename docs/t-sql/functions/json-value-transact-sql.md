---
title: JSON_VALUE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JSON_VALUE
- JSON_VALUE_TSQL
helpviewer_keywords:
- JSON_VALUE function
- JSON, extracting
- JSON, querying
ms.assetid: cd016e14-11eb-4eaf-bf05-c7cfcc820a10
caps.latest.revision: "18"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: ab4c14769dc51c6d5b97a6ad2fe6f0cb06fad4e0
ms.sourcegitcommit: 19e1c4067142d33e8485cb903a7a9beb7d894015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="jsonvalue-transact-sql"></a>JSON_VALUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Extrait une valeur scalaire à partir d’une chaîne JSON.  
  
 Pour extraire un objet ou un tableau à partir d’une chaîne JSON au lieu d’une valeur scalaire, consultez [JSON_QUERY &#40; Transact-SQL &#41; ](../../t-sql/functions/json-query-transact-sql.md). Pour plus d’informations sur les différences entre **JSON_VALUE** et **JSON_QUERY**, consultez [comparer les JSON_VALUE et JSON_QUERY](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md#JSONCompare).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
JSON_VALUE ( expression , path )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Expression. En règle générale, le nom d’une variable ou une colonne qui contient le texte JSON.  
 
 Si **JSON_VALUE** recherche JSON qui n’est pas valide dans *expression* avant de trouver la valeur identifiée par *chemin d’accès*, la fonction retourne une erreur. Si **JSON_VALUE* ne trouve pas la valeur identifiée par *chemin d’accès*, il analyse l’intégralité du texte et retourne une erreur si elle constate que JSON n’est pas valide, n’importe où dans *expression*.
  
 *chemin d’accès*  
 Un chemin d’accès JSON qui spécifie la propriété à extraire. Pour plus d’informations, consultez [Expressions de chemin JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
 
Dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] et dans [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], vous pouvez fournir une variable en tant que la valeur de *chemin d’accès*.
  
 Si le format de *chemin d’accès* n’est pas valide, **JSON_VALUE** renvoie une erreur.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne une valeur de texte unique de type nvarchar (4000). Le classement de la valeur retournée est le même que le classement de l’expression d’entrée.  
  
 Si la valeur est supérieure à 4 000 caractères :  
  
-   En mode de type lax, **JSON_VALUE** retourne la valeur null.  
  
-   En mode strict, **JSON_VALUE** renvoie une erreur.  
  
 Si vous disposez de plus de 4000 caractères retournent des valeurs scalaires, utilisez **OPENJSON** au lieu de **JSON_VALUE**. Pour plus d’informations, consultez [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
## <a name="remarks"></a>Notes

### <a name="lax-mode-and-strict-mode"></a>Mode souple et en mode strict

 Considérez le texte JSON suivant :  
  
```json  
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=N'{  
     "info":{    
       "type":1,  
       "address":{    
         "town":"Bristol",  
         "county":"Avon",  
         "country":"England"  
       },  
       "tags":["Sport", "Water polo"]  
    },  
    "type":"Basic"  
 }'  
```  
  
 Le tableau suivant compare le comportement de **JSON_VALUE** en mode de type lax et en mode strict. Pour plus d’informations sur la spécification du mode de chemin d’accès facultatif (lax ou stricte), consultez [Expressions de chemin JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|Chemin d'accès|Valeur de retour en mode lax|Valeur de retour en mode strict|En savoir plus|  
|----------|------------------------------|---------------------------------|---------------|  
|$|NULL|Erreur|Valeur scalaire.<br /><br /> Utilisez **JSON_QUERY** à la place.|  
|$. info.type|N '1'|N '1'|N/a|  
|$. info.address.town|N'Bristol'|N'Bristol'|N/a|  
|$.info. » adresse »|NULL|Erreur|Valeur scalaire.<br /><br /> Utilisez **JSON_QUERY** à la place.|  
|$. info.tags|NULL|Erreur|Valeur scalaire.<br /><br /> Utilisez **JSON_QUERY** à la place.|  
|$. info.type[0]|NULL|Erreur|Pas d’un tableau.|  
|$. info.none|NULL|Erreur|Propriété n’existe pas.|  
  
## <a name="examples"></a>Exemples  
  
### <a name="example-1"></a>Exemple 1  
 L’exemple suivant utilise les valeurs des propriétés JSON `town` et `state` dans les résultats de la requête. Étant donné que **JSON_VALUE** conserve le classement de la source, l’ordre de tri des résultats dépend du classement de la `jsonInfo` colonne. 

> [!NOTE]
> (Cet exemple suppose qu’une table nommée `Person.Person` contient un `jsonInfo` colonne de texte JSON, et que cette colonne est la structure présentée plus haut dans la description de type lax mode et le mode strict. Dans la base de données AdventureWorks, le `Person` table ne contient pas en fait un `jsonInfo` colonne.)
  
```sql  
SELECT FirstName, LastName,
 JSON_VALUE(jsonInfo,'$.info.address[0].town') AS Town
FROM Person.Person
WHERE JSON_VALUE(jsonInfo,'$.info.address[0].state') LIKE 'US%'
ORDER BY JSON_VALUE(jsonInfo,'$.info.address[0].town')
```  
  
### <a name="example-2"></a>Exemple 2  
 L’exemple suivant extrait la valeur de la propriété JSON `town` dans une variable locale.  
  
```sql  
DECLARE @jsonInfo NVARCHAR(MAX)
DECLARE @town NVARCHAR(32)

SET @jsonInfo=N'<array of address info>'

SET @town=JSON_VALUE(@jsonInfo,'$.info.address.town')
```  
  
### <a name="example-3"></a>Exemple 3  
 L’exemple suivant crée des colonnes calculées basées sur les valeurs des propriétés JSON.  
  
```sql  
CREATE TABLE dbo.Store
 (
  StoreID INT IDENTITY(1,1) NOT NULL,
  Address VARCHAR(500),
  jsonContent NVARCHAR(8000),
  Longitude AS JSON_VALUE(jsonContent, '$.address[0].longitude'),
  Latitude AS JSON_VALUE(jsonContent, '$.address[0].latitude')
 )
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de chemin JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [Données JSON &#40; SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  
