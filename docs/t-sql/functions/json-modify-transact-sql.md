---
title: JSON_MODIFY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 96bc8255-a037-4907-aec4-1a9c30814651
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 70f2c1456da6469c39389fada6a74ccf46383582
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="jsonmodify-transact-sql"></a>JSON_MODIFY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Met à jour la valeur d’une propriété dans une chaîne JSON et retourne la chaîne JSON mise à jour.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
JSON_MODIFY ( expression , path , newValue )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Expression. En règle générale, le nom d’une variable ou une colonne qui contient le texte JSON.  
  
 **JSON_MODIFY** renvoie une erreur si *expression* ne contient pas un JSON valide.  
  
 *chemin d’accès*  
 Une expression de chemin JSON qui spécifie la propriété à mettre à jour.

 *chemin d’accès* présente la syntaxe suivante :  
  
 `[append] [ lax | strict ] $.<json path>`  
  
-   *ajouter*  
    Modificateur facultatif qui spécifie que la nouvelle valeur doit être ajoutée au tableau référencé par  *\<chemin json >*.  
  
-   *lax*  
    Spécifie que la propriété référencée par  *\<chemin json >* ne doit pas nécessairement exister. Si la propriété n’est pas présente, JSON_MODIFY tente d’insérer la nouvelle valeur du chemin d’accès spécifié. Insertion peut échouer si la propriété ne peut pas être insérée sur le chemin d’accès. Si vous ne spécifiez pas *lax* ou *strict*, *lax* est le mode par défaut.  
  
-   *strict*  
    Spécifie que la propriété référencée par  *\<chemin json >* doit être dans l’expression de JSON. Si la propriété n’est pas présente, JSON_MODIFY renvoie une erreur.  
  
-   *\<chemin d’accès JSON >*  
    Spécifie le chemin d’accès de la propriété à mettre à jour. Pour plus d’informations, consultez [Expressions de chemin JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
Dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] et dans [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], vous pouvez fournir une variable en tant que la valeur de *chemin d’accès*.

**JSON_MODIFY** renvoie une erreur si le format de *chemin d’accès* n’est pas valide.  
  
 *nouvelle valeur*  
 La nouvelle valeur de la propriété spécifiée par *chemin d’accès*.  
  
 En mode de type lax, JSON_MODIFY supprime la clé spécifiée, si la nouvelle valeur est NULL.  
  
JSON_MODIFY remplace tous les caractères spéciaux dans la nouvelle valeur si le type de la valeur est NVARCHAR ou VARCHAR. Une valeur de texte non échappée s’il est correctement au format JSON produite par FOR JSON, JSON_QUERY ou JSON_MODIFY.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne la valeur mise à jour de *expression* comme correctement mis en forme de texte JSON.  
  
## <a name="remarks"></a>Notes  
 La fonction JSON_MODIFY vous permet de mettre à jour la valeur d’une propriété existante, insérez une nouvelle paire clé-valeur ou supprimer une clé basée sur une combinaison de modes et les valeurs fournies.  
  
 Le tableau suivant compare le comportement de **JSON_MODIFY** en mode de type lax et en mode strict. Pour plus d’informations sur la spécification du mode de chemin d’accès facultatif (lax ou stricte), consultez [Expressions de chemin JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|Valeur existante|Chemin d’accès existe|Mode lax|Mode strict|  
|--------------------|-----------------|--------------|-----------------|  
|Non NULL|Oui|Mettre à jour la valeur existante.|Mettre à jour la valeur existante.|  
|Non NULL|Non|Essayez de créer une nouvelle paire clé-valeur sur le chemin d’accès spécifié.<br /><br /> Cette opération peut échouer. Par exemple, si vous spécifiez le chemin d’accès `$.user.setting.theme`, JSON_MODIFY n’insère pas de la clé `theme` si le `$.user` ou `$.user.settings` objets n’existent pas, ou si les paramètres est un tableau ou une valeur scalaire.|Erreur : INVALID_PROPERTY|  
|NULL|Oui|Supprimer la propriété existante.|Définir la valeur null.|  
|NULL|Non|Aucune action. Le premier argument est retourné comme résultat.|Erreur : INVALID_PROPERTY|  
  
 En mode de type lax, JSON_MODIFY tente de créer une nouvelle paire clé-valeur, mais dans certains cas, il peut échouer.  
  
## <a name="examples"></a>Exemples  
  
### <a name="example---basic-operations"></a>Exemple : opérations de base  
 L’exemple suivant montre les opérations de base qui peuvent être faites avec le texte JSON.  
  
 **Requête**  
  
```sql  

DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update name  

SET @info=JSON_MODIFY(@info,'$.name','Mike')

PRINT @info

-- Insert surname  

SET @info=JSON_MODIFY(@info,'$.surname','Smith')

PRINT @info

-- Delete name  

SET @info=JSON_MODIFY(@info,'$.name',NULL)

PRINT @info

-- Add skill  

SET @info=JSON_MODIFY(@info,'append $.skills','Azure')

PRINT @info
```  
  
 **Résultats**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL"],
    "surname": "Smith"
} {
    "skills": ["C#", "SQL"],
    "surname": "Smith"
} {
    "skills": ["C#", "SQL", "Azure"],
    "surname": "Smith"
}
```  
  
### <a name="example---multiple-updates"></a>Exemple - plusieurs mises à jour  
 Avec JSON_MODIFY, vous pouvez mettre à jour qu’une seule propriété. Si vous devez effectuer plusieurs mises à jour, vous pouvez utiliser plusieurs appels JSON_MODIFY.  
  
 **Requête**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Multiple updates  

SET @info=JSON_MODIFY(JSON_MODIFY(JSON_MODIFY(@info,'$.name','Mike'),'$.surname','Smith'),'append $.skills','Azure')

PRINT @info
```  
  
 **Résultats**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL", "Azure"],
    "surname": "Smith"
}
```  
  
### <a name="example---rename-a-key"></a>Exemple : renommer une clé  
 L’exemple suivant montre comment renommer une propriété dans un texte JSON avec la fonction JSON_MODIFY. Tout d’abord, vous pouvez prendre la valeur d’une propriété existante et insérer en tant qu’une nouvelle paire clé-valeur. Vous pouvez supprimer l’ancienne clé en définissant la valeur de l’ancienne propriété NULL.  
  
 **Requête**  
  
```sql  
DECLARE @product NVARCHAR(100)='{"price":49.99}'

PRINT @product

-- Rename property  

SET @product=
 JSON_MODIFY(
  JSON_MODIFY(@product,'$.Price',CAST(JSON_VALUE(@product,'$.price') AS NUMERIC(4,2))),
  '$.price',
  NULL
 )

PRINT @product
```  
  
 **Résultats**  
  
```json  
{
    "price": 49.99
} {
    "Price": 49.99
}
```  
  
 Si vous n’effectuez un cast de la nouvelle valeur à un type numérique, JSON_MODIFY traite en tant que texte et il entoure avec des guillemets doubles.  
  
### <a name="example---increment-a-value"></a>Exemple : une valeur d’incrément  
 L’exemple suivant montre comment incrémenter la valeur d’une propriété dans un texte JSON avec la fonction JSON_MODIFY. Tout d’abord, vous pouvez prendre la valeur de la propriété existante et insérer en tant qu’une nouvelle paire clé-valeur. Vous pouvez supprimer l’ancienne clé en définissant la valeur de l’ancienne propriété NULL.  
  
 **Requête**  
  
```sql  
DECLARE @stats NVARCHAR(100)='{"click_count": 173}'

PRINT @stats

-- Increment value  

SET @stats=JSON_MODIFY(@stats,'$.click_count',
 CAST(JSON_VALUE(@stats,'$.click_count') AS INT)+1)

PRINT @stats
```  
  
 **Résultats**  
  
```json  
{
    "click_count": 173
} {
    "click_count": 174
}
```  
  
### <a name="example---modify-a-json-object"></a>Exemple : modification d’un objet JSON  
 JSON_MODIFY traite le *newValue* argument sous forme de texte brut même si elle contient correctement mis en forme le texte JSON. Par conséquent, la sortie JSON de la fonction est entourée de guillemets doubles et tous les caractères spéciaux sont échappés, comme indiqué dans l’exemple suivant.  
  
 **Requête**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update skills array

SET @info=JSON_MODIFY(@info,'$.skills','["C#","T-SQL","Azure"]')

PRINT @info
```  
  
 **Résultats**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "John",
    "skills": "["C#","T-SQL","Azure"]"
}
```  
  
 Pour éviter la séquence d’échappement automatique, fournissez *newValue* à l’aide de la fonction JSON_QUERY. JSON_MODIFY sait que la valeur retournée par JSON_MODIFY est correctement au format JSON, donc il n’échappe pas la valeur.  
  
 **Requête**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update skills array  

SET @info=JSON_MODIFY(@info,'$.skills',JSON_QUERY('["C#","T-SQL","Azure"]'))

PRINT @info
```  
  
 **Résultats**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "John",
    "skills": ["C#", "T-SQL", "Azure"]
}
```  
  
### <a name="example---update-a-json-column"></a>Exemple : mise à jour une colonne JSON  
 L’exemple suivant met à jour la valeur d’une propriété dans une colonne de table qui contient des données JSON.  
  
```sql  
UPDATE Employee
SET jsonCol=JSON_MODIFY(jsonCol,"$.info.address.town",'London')
WHERE EmployeeID=17
 
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de chemin JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [Données JSON &#40; SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  

