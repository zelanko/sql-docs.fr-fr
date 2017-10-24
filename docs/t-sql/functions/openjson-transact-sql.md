---
title: OPENJSON (Transact-SQL) | Documents Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENJSON
- OPENJSON_TSQL
helpviewer_keywords:
- OPENJSON rowset function
- JSON, importing
- JSON, converting from
ms.assetid: 233d0877-046b-4dcc-b5da-adeb22f78531
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 29b296b2ae7e04871e81a9c236cb990bdd19562b
ms.openlocfilehash: 27eeb54d6493bb200e56caada1238d6fafb5b339
ms.contentlocale: fr-fr
ms.lasthandoff: 10/11/2017

---
# <a name="openjson-transact-sql"></a>OPENJSON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

**OPENJSON** est une fonction table qui analyse le texte JSON et retourne des objets et propriétés de l’entrée JSON en lignes et colonnes. En d’autres termes, **OPENJSON** fournit une vue d’ensemble de lignes sur un document JSON. Vous pouvez spécifier explicitement les colonnes dans l’ensemble de lignes et les chemins d’accès de propriété JSON permet de remplir les colonnes. Étant donné que **OPENJSON** retourne un ensemble de lignes, vous pouvez utiliser **OPENJSON** dans les `FROM` clause d’un [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction tout comme vous pouvez utiliser n’importe quel autre table, vue ou fonction table.  
  
Utilisez **OPENJSON** pour importer des données JSON dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou pour convertir des données JSON au format relationnel pour une application ou un service ne peut pas utiliser JSON directement.  
  
> [!NOTE]  
>  Le **OPENJSON** fonction est disponible uniquement au niveau de compatibilité 130 ou une version ultérieure. Si le niveau de compatibilité de votre base de données est inférieur à 130, SQL Server ne peut pas trouver ni exécuter la fonction **OPENJSON**. Les autres fonctions JSON sont disponibles à tous les niveaux de compatibilité.
> 
> Vous pouvez vérifier le niveau de compatibilité dans la vue `sys.databases` ou dans les propriétés de base de données. Vous pouvez modifier le niveau de compatibilité de base de données avec la commande suivante :  
> 
> `ALTER DATABASE DatabaseName SET COMPATIBILITY_LEVEL = 130`
>   
> Niveau de compatibilité 120 peut être la valeur par défaut, même dans une nouvelle base de données SQL Azure.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique")[Conventions de syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
OPENJSON( jsonExpression [ , path ] )  [ <with_clause> ]

<with_clause> ::= WITH ( { colName type [ column_path ] [ AS JSON ] } [ ,...n ] )
```  

Le **OPENJSON** fonction table analyse la *jsonExpression* fourni comme premier argument et retourne une ou plusieurs lignes contenant des données à partir des objets JSON dans l’expression. *jsonExpression* peut contenir des sous-objets imbriqués. Si vous souhaitez analyser un sous-objet depuis *jsonExpression*, vous pouvez spécifier un **chemin d’accès** paramètre pour le sous-objet JSON.

### <a name="openjson"></a>openjson

![Syntaxe de OPENJSON TVF](../../relational-databases/json/media/openjson-syntax.png "une syntaxe OPENJSON")  

Par défaut, le **OPENJSON** fonction table retourne trois colonnes qui contiennent le nom de clé, la valeur, et le type de chaque paire {clé : valeur} trouvé dans *jsonExpression*. En guise d’alternative, vous pouvez spécifier explicitement dans le schéma du résultat que la valeur **OPENJSON** retourne en fournissant *with_clause*.
  
### <a name="withclause"></a>with_clause
  
![Syntaxe d’avec la clause dans OPENJSON TVF](../../relational-databases/json/media/openjson-shema-syntax.png "OPENJSON avec la syntaxe")

*with_clause* contient une liste de colonnes avec leurs types de **OPENJSON** à retourner. Par défaut, **OPENJSON** correspond aux clés dans *jsonExpression* avec les noms de colonnes dans *with_clause* (dans ce cas, les clés de correspondances implique qu’il est respecte la casse). Si un nom de colonne ne correspond pas à un nom de clé, vous pouvez fournir un texte facultatif *column_path*, qui est un [Expression de chemin JSON](../../relational-databases/json/json-path-expressions-sql-server.md) qui fait référence à une clé dans le *jsonExpression*. 

## <a name="arguments"></a>Arguments  
### <a name="jsonexpression"></a>*jsonExpression*  
Est une expression de caractères Unicode contenant le texte JSON.  
  
OPENJSON effectue une itération sur les éléments du tableau ou les propriétés de l’objet dans l’expression de JSON et renvoie une ligne pour chaque élément ou la propriété. L’exemple suivant retourne chaque propriété de l’objet fourni en tant que *jsonExpression*:  
  
```sql  
DECLARE @json NVARCHAR(4000) = N'{  
   "StringValue":"John",  
   "IntValue":45,  
   "TrueValue":true,  
   "FalseValue":false,  
   "NullValue":null,  
   "ArrayValue":["a","r","r","a","y"],  
   "ObjectValue":{"obj":"ect"}  
}'

SELECT *
FROM OPENJSON(@json)
```  
  
**Résultats**  
  
|Clé|valeur|Type|  
|---------|-----------|----------|  
|StringValue|John|1|  
|IntValue|45|2|  
|trueValue|true|3|  
|falseValue|false|3|  
|nullValue|NULL|0|  
|ArrayValue|[« a », « r », « r », « un «, » y »]|4|  
|ObjectValue|{« obj » : « ect »}|5|  

### <a name="path"></a>*chemin d’accès*  
Est une expression de chemin d’accès JSON facultatif qui fait référence à un objet ou un tableau dans *jsonExpression*. **OPENJSON** recherches dans le texte JSON à la position spécifiée et analyse uniquement le fragment référencé. Pour plus d’informations, consultez [Expressions de chemin JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).

Dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] et dans [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], vous pouvez fournir une variable en tant que la valeur de *chemin d’accès*.
  
L’exemple suivant retourne un objet imbriqué en spécifiant le *chemin d’accès*:  

```sql  
DECLARE @json NVARCHAR(4000) = N'{  
      "path": {  
            "to":{  
                 "sub-object":["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]  
                 }  
              }  
 }';

SELECT [key], value
FROM OPENJSON(@json,'$.path.to."sub-object"')
```  
  
 **Résultats**  
  
|Clé|Valeur|  
|---------|-----------|  
|0|en-GB|  
|1|en-UK|  
|2|de-AT|  
|3|es-AR|  
|4|sr-Cyrl|  
 
Lorsque **OPENJSON** analyse un tableau JSON, la fonction retourne l’index des éléments dans le texte JSON en tant que clés.

La comparaison utilisée pour faire correspondre les étapes de chemin d’accès avec les propriétés de l’expression de JSON respecte la casse et classement ne dépendant pas (autrement dit, une comparaison BIN2). 

### <a name="withclause"></a>*with_clause*
Définit explicitement le schéma de sortie pour le **OPENJSON** fonction à retourner. Le paramètre facultatif *with_clause* peut contenir les éléments suivants :

*nom de colonne* est le nom de la colonne de sortie.  
  
Par défaut, **OPENJSON** utilise le nom de la colonne qui correspond à une propriété dans le texte JSON. Par exemple, si vous spécifiez la colonne *nom* dans le schéma, OPENJSON essaie de remplir cette colonne avec la propriété « name » dans le texte JSON. Vous pouvez remplacer ce mappage par défaut à l’aide de la *column_path* argument.  
  
*type*  
Est le type de données pour la colonne de sortie.  

> [!NOTE]
> Si vous utilisez également le **AS JSON** option, la colonne *type* doit être `NVARCHAR(MAX)`.
  
*column_path*  
Est le chemin d’accès JSON qui spécifie la propriété à retourner dans la colonne spécifiée. Pour plus d’informations, consultez la description de la *chemin d’accès* paramètre précédemment dans cette rubrique.  
  
Utilisez *column_path* pour remplacer les règles de mappage par défaut lorsque le nom d’une colonne de sortie ne correspond pas à celui de la propriété.  
  
La comparaison utilisée pour faire correspondre les étapes de chemin d’accès avec les propriétés de l’expression de JSON respecte la casse et classement ne dépendant pas (autrement dit, une comparaison BIN2).  
  
Pour plus d’informations sur les chemins d’accès, consultez [Expressions de chemin JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
*EN TANT QUE JSON*  
Utilisez le **AS JSON** option dans une définition de colonne pour spécifier que la propriété référencée contient un objet JSON interne ou un tableau. Si vous spécifiez la **AS JSON** option, le type de la colonne doit être nvarchar (max).

-   Si vous ne spécifiez pas **AS JSON** pour une colonne, la fonction retourne une valeur scalaire (par exemple, int, string, la valeur true, false) à partir de la propriété JSON spécifiée sur le chemin d’accès spécifié. Si le chemin d’accès représente un objet ou un tableau, et que la propriété est introuvable dans le chemin d’accès spécifié, la fonction retourne la valeur null en mode lax ou retourne une erreur en mode strict. Ce comportement est semblable au comportement de la **JSON_VALUE** (fonction).  
  
-   Si vous spécifiez **AS JSON** pour une colonne, la fonction retourne un fragment JSON à partir de la propriété JSON spécifiée sur le chemin d’accès spécifié. Si le chemin d’accès représente une valeur scalaire, et la propriété est introuvable dans le chemin d’accès spécifié, la fonction retourne la valeur null en mode lax ou retourne une erreur en mode strict. Ce comportement est semblable au comportement de la **JSON_QUERY** (fonction).  
  
> [!NOTE]  
> Si vous souhaitez renvoyer un fragment JSON imbriqué à partir d’une propriété JSON, vous devez fournir le **AS JSON** indicateur. Sans cette option, si la propriété ne peut pas être trouvée, OPENJSON retourne une valeur NULL au lieu de l’objet JSON référencé ou d’un tableau, ou elle retourne une erreur d’exécution en mode strict.  
  
Par exemple, la requête suivante retourne et met en forme les éléments d’un tableau :  
  
```sql  
DECLARE @json NVARCHAR(MAX) = N'[  
  {  
    "Order": {  
      "Number":"SO43659",  
      "Date":"2011-05-31T00:00:00"  
    },  
    "AccountNumber":"AW29825",  
    "Item": {  
      "Price":2024.9940,  
      "Quantity":1  
    }  
  },  
  {  
    "Order": {  
      "Number":"SO43661",  
      "Date":"2011-06-01T00:00:00"  
    },  
    "AccountNumber":"AW73565",  
    "Item": {  
      "Price":2024.9940,  
      "Quantity":3  
    }  
  }
]'  
   
SELECT *
FROM OPENJSON ( @json )  
WITH (   
              Number   varchar(200)   '$.Order.Number',  
              Date     datetime       '$.Order.Date',  
              Customer varchar(200)   '$.AccountNumber',  
              Quantity int            '$.Item.Quantity',  
              [Order]  nvarchar(MAX)  AS JSON  
 )
```  
  
**Résultats**  
  
|Number|Date|Customer|Quantité|JSON|  
|------------|----------|--------------|--------------|-----------|  
|SO43659|2011-05-31T00:00:00|AW29825|1|{« Nombre » : « SO43659 », « Date » : « 2011-05-31T00:00:00 »}|  
|SO43661|2011-06-01T00:00:00|AW73565|3|{« Nombre » : « SO43661 », « Date » : « 2011-06-01T00:00:00 »}|  
  

## <a name="return-value"></a>Valeur retournée  
Les colonnes que la fonction OPENJSON retourne dépendent de l’option WITH.  
  
1. Lorsque vous appelez OPENJSON avec le schéma par défaut - autrement dit, lorsque vous ne spécifiez pas un schéma explicite dans la clause WITH - la fonction retourne une table comportant les colonnes suivantes :  
    1.  **Clé**. Une valeur nvarchar (4000) qui contient le nom de la propriété spécifiée ou de l’index de l’élément dans le tableau spécifié. La colonne clé a un classement BIN2.  
    2.  **Valeur**. Une valeur nvarchar (max) qui contient la valeur de la propriété. La colonne valeur hérite son classement de *jsonExpression*.
    3.  **Type**. Une valeur d’entier qui contient le type de la valeur. Le **Type** colonne est retournée uniquement lorsque vous utilisez OPENJSON avec le schéma par défaut. La colonne de type a l’une des valeurs suivantes :  
  
        |Valeur de la colonne de Type|Type de données JSON|  
        |------------------------------|--------------------|  
        |0|Null|  
        |1|chaîne|  
        |2|int|  
        |3|la valeur true/false|  
        |4|tableau|  
        |5|objet|  
  
     Uniquement les propriétés de premier niveau sont retournées. L’instruction échoue si le texte JSON n’est pas formaté correctement.  

2. Lorsque vous appelez OPENJSON et spécifiez un schéma explicite dans la clause WITH, la fonction retourne une table avec le schéma que vous avez définie dans la clause WITH.  

## <a name="remarks"></a>Notes  

*json_path* utilisé dans le deuxième argument de **OPENJSON** ou dans *with_clause* peut commencer par le **lax** ou **strict** (mot clé).

-   Dans **lax** mode, **OPENJSON** ne déclenche pas une erreur si l’objet ou la valeur du chemin d’accès spécifié est introuvable. Si le chemin d’accès ne peut pas être trouvée, **OPENJSON** retourne un jeu de résultats vide ou une valeur NULL.
-   Dans **strict**, mode **OPENJSON** renvoie une erreur si le chemin d’accès est introuvable.

Certains exemples de cette page spécifient explicitement le mode path, lax ou strict. Le mode de chemin d’accès est facultatif. Si vous ne spécifiez pas explicitement un mode path, mode lax est la valeur par défaut. Pour plus d’informations sur le mode de chemin d’accès et les expressions de chemin d’accès, consultez [Expressions de chemin JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).    

Noms de colonne dans *with_clause* sont mises en correspondance avec des clés dans le texte JSON. Si vous spécifiez le nom de colonne `[Address.Country]`, il est mis en correspondance avec la clé `Address.Country`. Si vous souhaitez faire référence à une clé imbriquée `Country` au sein de l’objet `Address`, vous devez spécifier le chemin d’accès `$.Address.Country` dans le chemin d’accès de la colonne.

*json_path* peut contenir des clés avec des caractères alphanumériques. Séquence d’échappement dans le nom de la clé *json_path* avec des guillemets doubles si vous avez des caractères spéciaux dans les clés. Par exemple, `$."my key $1".regularKey."key with . dot"` correspond à la valeur 1 dans le texte JSON suivant :

```json
{
  "my key $1": {
    "regularKey":{
      "key with . dot": 1
    }
  }
}
```  

## <a name="examples"></a>Exemples  
  
### <a name="example-1---convert-a-json-array-to-a-temporary-table"></a>Exemple 1 : convertir un tableau JSON dans une table temporaire  
L’exemple suivant fournit une liste d’identificateurs en un tableau JSON de nombres. La requête convertit le tableau JSON à une table d’identificateurs et filtre tous les produits avec les ID spécifiés.  
  
```sql  
DECLARE @pSearchOptions NVARCHAR(4000) = N'[1,2,3,4]'

SELECT *
FROM products
INNER JOIN OPENJSON(@pSearchOptions) AS productTypes
 ON product.productTypeID = productTypes.value
```  
  
Cette requête est équivalente à l’exemple suivant. Toutefois, dans l’exemple ci-dessous, vous devez incorporer des nombres dans la requête au lieu de les passer en tant que paramètres.  
  
```sql  
SELECT *
FROM products
WHERE product.productTypeID IN (1,2,3,4)
```  
  
### <a name="example-2---merge-properties-from-two-json-objects"></a>Exemple 2 - propriétés de la fusion de deux objets JSON  
L’exemple suivant sélectionne une union de toutes les propriétés de deux objets JSON. Les deux objets ont un double *nom* propriété. L’exemple utilise la valeur de clé à exclure de la ligne en double dans les résultats.  
  
```sql  
DECLARE @json1 NVARCHAR(MAX),@json2 NVARCHAR(MAX)

SET @json1=N'{"name": "John", "surname":"Doe"}'

SET @json2=N'{"name": "John", "age":45}'

SELECT *
FROM OPENJSON(@json1)
UNION ALL
SELECT *
FROM OPENJSON(@json2)
WHERE [key] NOT IN (SELECT [key] FROM OPENJSON(@json1))
```  
  
### <a name="example-3---join-rows-with-json-data-stored-in-table-cells-using-cross-apply"></a>Exemple 3 : lignes de jointure avec des données JSON stockées dans les cellules de tableau à l’aide de CROSS APPLY  
Dans l’exemple suivant, la `SalesOrderHeader` table a un `SalesReason` colonne de texte qui contient un tableau de `SalesOrderReasons` au format JSON. Le `SalesOrderReasons` objets contiennent des propriétés telles que *qualité* et *fabricant*. L’exemple crée un rapport qui relie chaque ligne de commande client au motif de vente. L’opérateur OPENJSON développe le tableau JSON de motifs de vente comme si les motifs étaient stockés dans une table enfant distincte. Puis l’opérateur CROSS APPLY relie chaque ligne de commande client aux lignes retournées par la fonction table OPENJSON.  
  
```sql  
SELECT SalesOrderID,OrderDate,value AS Reason
FROM Sales.SalesOrderHeader
CROSS APPLY OPENJSON(SalesReasons)
```  
  
> [!TIP] 
> Lorsque vous devez développer tableaux JSON stocké dans des champs individuels et les joindre avec leurs lignes parent, vous utilisez généralement la [!INCLUDE[tsql](../../includes/tsql-md.md)] opérateur CROSS APPLY. Pour plus d’informations sur CROSS APPLY, consultez [FROM &#40; Transact-SQL &#41; ](../../t-sql/queries/from-transact-sql.md).  
  
La même requête peut être réécrit à l’aide de `OPENJSON` avec un schéma explicitement défini de lignes à retourner :  
  
```sql  
SELECT SalesOrderID, OrderDate, value AS Reason  
FROM Sales.SalesOrderHeader  
     CROSS APPLY OPENJSON (SalesReasons) WITH (value nvarchar(100) '$')
```  
  
Dans cet exemple, le `$` chemin d’accès fait référence à chaque élément du tableau. Si vous souhaitez convertir explicitement la valeur retournée, vous pouvez utiliser ce type de requête.  
  
### <a name="example-4---combine-relational-rows-and-json-elements-with-cross-apply"></a>Exemple 4 : combiner des lignes relationnelles et des éléments JSON avec CROSS APPLY  
La requête suivante combine les lignes relationnelles et des éléments JSON dans les résultats présentés dans le tableau suivant.  
  
```sql  
SELECT store.title, location.street, location.lat, location.long  
FROM store  
CROSS APPLY OPENJSON(store.jsonCol, 'lax $.location')   
     WITH (street varchar(500) ,  postcode  varchar(500) '$.postcode' ,  
     lon int '$.geo.longitude', lat int '$.geo.latitude')  
     AS location
```  
  
**Résultats**  
  
|title|street|code postal|LON|table d’adresses locales|  
|-----------|------------|--------------|---------|---------|  
|Ensemble de produits alimentaires marchés|Moyen de Redmond 17991|WA 98052|47.666124|-122.10155|  
|Sears|148th Ave nou|WA 98052|47.63024|-122.141246,17|  
  
### <a name="example-5---import-json-data-into-sql-server"></a>Exemple 5 : importer des données JSON dans SQL Server  
L’exemple suivant charge l’intégralité d’un objet JSON dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```sql  
DECLARE @json NVARCHAR(max)  = N'{  
  "id" : 2,  
  "firstName": "John",  
  "lastName": "Smith",  
  "isAlive": true,  
  "age": 25,  
  "dateOfBirth": "2015-03-25T12:00:00",  
  "spouse": null  
  }';  
   
  INSERT INTO Person  
  SELECT *   
  FROM OPENJSON(@json)  
  WITH (id int,  
        firstName nvarchar(50), lastName nvarchar(50),   
        isAlive bit, age int,  
        dateOfBirth datetime2, spouse nvarchar(50)
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de chemin JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [Convertir des données JSON en lignes et colonnes avec OPENJSON &#40; SQL Server &#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)   
 [Utiliser OPENJSON avec le schéma par défaut &#40; SQL Server &#41;](../../relational-databases/json/use-openjson-with-the-default-schema-sql-server.md)   
 [Utilisation d’OPENJSON avec un schéma explicite &#40; SQL Server &#41;](../../relational-databases/json/use-openjson-with-an-explicit-schema-sql-server.md)  
  
  

