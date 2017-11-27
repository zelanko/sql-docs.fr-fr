---
title: JSON_QUERY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/02/2016
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
- JSON_QUERY
- JSON_QUERY_TSQL
helpviewer_keywords:
- JSON, extracting
- JSON, querying
- JSON_QUERY function
ms.assetid: 1ab0d90f-19b6-4988-ab4f-22fdf28b7c79
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 310d85e26226cd54eff5d1c99e94b235348a90f7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="jsonquery-transact-sql"></a>JSON_QUERY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Extrait un objet ou un tableau à partir d’une chaîne JSON.  
  
 Pour extraire une valeur scalaire à partir d’une chaîne JSON au lieu d’un objet ou un tableau, consultez [JSON_VALUE &#40; Transact-SQL &#41; ](../../t-sql/functions/json-value-transact-sql.md). Pour plus d’informations sur les différences entre **JSON_VALUE** et **JSON_QUERY**, consultez [comparer les JSON_VALUE et JSON_QUERY](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md#JSONCompare).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
JSON_QUERY ( expression [ , path ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Expression. En règle générale, le nom d’une variable ou une colonne qui contient le texte JSON.  
  
 Si **JSON_QUERY** recherche JSON qui n’est pas valide dans *expression* avant de trouver la valeur identifiée par *chemin d’accès*, la fonction retourne une erreur. Si **JSON_QUERY** ne trouve pas la valeur identifiée par *chemin d’accès*, il analyse l’intégralité du texte et retourne une erreur si elle constate que JSON n’est pas valide, n’importe où dans *expression*.  
  
 *chemin d’accès*  
 Un chemin d’accès JSON qui spécifie l’objet ou le tableau à extraire.

Dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] et dans [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], vous pouvez fournir une variable en tant que la valeur de *chemin d’accès*.

Le chemin d’accès JSON permettre spécifier le mode de lax ou strict pour l’analyse. Si vous ne spécifiez pas le mode d’analyse, mode lax est la valeur par défaut. Pour plus d’informations, consultez [Expressions de chemin JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  

La valeur par défaut *chemin d’accès* est '$'. Par conséquent, si vous ne fournissez pas une valeur pour *chemin d’accès*, **JSON_QUERY** retourne l’entrée *expression*.

Si le format de *chemin d’accès* n’est pas valide, **JSON_QUERY** renvoie une erreur.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un fragment JSON de type nvarchar (max). Le classement de la valeur retournée est le même que le classement de l’expression d’entrée.  
  
 Si la valeur n’est pas un objet ou un tableau :  
  
-   En mode de type lax, **JSON_QUERY** retourne la valeur null.  
  
-   En mode strict, **JSON_QUERY** renvoie une erreur.  
  
## <a name="remarks"></a>Notes  

### <a name="lax-mode-and-strict-mode"></a>Mode souple et en mode strict

 Considérez le texte JSON suivant :  
  
```json  
{
    "info": {
        "type": 1,
        "address": {
            "town": "Bristol",
            "county": "Avon",
            "country": "England"
        },
        "tags": ["Sport", "Water polo"]
    },
    "type": "Basic"
} 
```  
  
 Le tableau suivant compare le comportement de **JSON_QUERY** en mode de type lax et en mode strict. Pour plus d’informations sur la spécification du mode de chemin d’accès facultatif (lax ou stricte), consultez [Expressions de chemin JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|Chemin d'accès|Valeur de retour en mode lax|Valeur de retour en mode strict|En savoir plus|  
|----------|------------------------------|---------------------------------|---------------|  
|$|Retourne l’intégralité du texte JSON.|Retourne l’intégralité du texte JSON.|N/a|  
|$. info.type|NULL|Erreur|Pas un objet ou un tableau.<br /><br /> Utilisez **JSON_VALUE** à la place.|  
|$. info.address.town|NULL|Erreur|Pas un objet ou un tableau.<br /><br /> Utilisez **JSON_VALUE** à la place.|  
|$.info. » adresse »|N'{« ville » : « Bristol », « région » : « Avon », « pays » : « Angleterre »} »|N'{« ville » : « Bristol », « région » : « Avon », « pays » : « Angleterre »} »|N/a|  
|$. info.tags|N « [« Sport », « Eau polo »] »|N « [« Sport », « Eau polo »] »|N/a|  
|$. info.type[0]|NULL|Erreur|Pas d’un tableau.|  
|$. info.none|NULL|Erreur|Propriété n’existe pas.|  

### <a name="using-jsonquery-with-for-json"></a>À l’aide de JSON_QUERY avec FOR JSON

**JSON_QUERY** renvoie un fragment JSON valid. Par conséquent, **FOR JSON** n’échappe les caractères spéciaux dans le **JSON_QUERY** valeur de retour.

Si vous renvoyez les résultats avec FOR JSON, et que vous insérez des données qui sont déjà au format JSON (dans une colonne ou le résultat d’une expression), retour à la ligne les données JSON avec **JSON_QUERY** sans le *chemin d’accès* paramètre.

## <a name="examples"></a>Exemples  
  
### <a name="example-1"></a>Exemple 1  
 L’exemple suivant montre comment renvoyer un fragment JSON dans un `CustomFields` colonne dans les résultats de la requête.  
  
```sql  
SELECT PersonID,FullName,
 JSON_QUERY(CustomFields,'$.OtherLanguages') AS Languages
FROM Application.People
```  
  
### <a name="example-2"></a>Exemple 2  
L’exemple suivant montre comment inclure les fragments JSON dans la sortie de la clause FOR JSON.  
  
```sql  
SELECT StockItemID, StockItemName,
         JSON_QUERY(Tags) as Tags,
         JSON_QUERY(CONCAT('["',ValidFrom,'","',ValidTo,'"]')) ValidityPeriod
FROM Warehouse.StockItems
FOR JSON PATH
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de chemin JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [Données JSON &#40; SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
