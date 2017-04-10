---
title: "Expressions de chemin JSON (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JSON, expressions de chemin"
  - "expressions de chemin (JSON)"
ms.assetid: 25ea679c-84cc-4977-867c-2cbe9d192553
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Expressions de chemin JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Utilisez les chemins JSON pour référencer les propriétés des objets JSON. Les chemins JSON utilisent une syntaxe similaire à Javascript.  
  
 Vous devez fournir une expression de chemin lorsque vous appelez les fonctions suivantes.  
  
-   Lorsque vous appelez **OPENJSON** pour créer une vue relationnelle des données JSON. Pour plus d’informations, consultez [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
-   Quand vous appelez **JSON_VALUE** pour extraire une valeur de texte JSON. Pour plus d’informations, consultez [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md).  
  
-   Quand vous appelez **JSON_QUERY** pour extraire un tableau ou un objet JSON. Pour plus d’informations, consultez [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md).  
  
-   Quand vous appelez **JSON_MODIFY** pour mettre à jour la valeur d’une propriété dans une chaîne JSON. Pour plus d’informations, consultez [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md).  
  
 Une expression de chemin comporte deux composants.  
  
1.  Le [mode PATH](#PATHMODE)facultatif, lax ou strict.  
  
2.  Le [chemin](#PATH) lui-même.  
  
##  <a name="PATHMODE"></a> mode PATH  
 Au début de l’expression de chemin, vous pouvez éventuellement déclarer le mode PATH en spécifiant le mot clé **lax** ou **strict**. La valeur par défaut est **lax**.  
  
-   En mode **lax** , les fonctions renvoient des valeurs vides si l’expression de chemin contient une erreur. Par exemple, si vous demandez la valeur **$.name**, et que le texte JSON ne contient pas de clé **name** , la fonction renvoie la valeur Null.  
  
-   En mode **strict** , les fonctions déclenchent des erreurs si l’expression de chemin contient une erreur.  
  
##  <a name="PATH"></a> chemin  
 Après la déclaration de mode de chemin facultatif, spécifiez le chemin lui-même.  
  
-   Le signe dollar ($) représente l’élément de contexte.  
  
-   Le chemin de la propriété est un ensemble d’étapes de chemin. Les étapes de chemin peuvent contenir les éléments et les opérateurs suivants.  
  
    -   Noms de clés. Si le nom de clé commence par un signe dollar ou contient des caractères spéciaux tels que des espaces, placez-le entre guillemets. Par exemple, `$.name` et `$."first name"`.  
  
    -   Éléments du tableau. Par exemple, `$.product[3]`. Les tableaux sont de base zéro.  
  
    -   L’opérateur point (.) indique un membre d’un objet.  
  
## Exemples  
 Les exemples de cette section font référence au texte JSON suivant.  
  
```json  
{ "people":  
  [  
    { "name": "John", "surname": "Doe" },  
    { "name": "Jane", "surname": null, "active": true }  
  ]  
}  
```  
  
 Le tableau suivant présente des exemples d’expressions de chemin.  
  
|Expression de chemin|Valeur|  
|---------------------|-----------|  
|$.people[0].name|John|  
|$.people[1]|{ "name": "Jane",  "surname": null, "active": true }|  
|$.people[1].surname|Null|  
|$|{ "people": [ { "name": "John",  "surname": "Doe" },<br />   { "name": "Jane",  "surname": null, "active": true } ] }|  
  
## Traitement des chemins en doublon  
 Si le texte JSON contient des propriétés en doublon (par exemple, deux clés portant le même nom sur le même niveau), les fonctions JSON_VALUE et JSON_QUERY renvoie la première valeur correspondant au chemin. Pour analyser un objet JSON contenant des clés en doublon, utilisez OPENJSON, comme illustré dans l’exemple suivant.  
  
```tsql  
DECLARE @json NVARCHAR(MAX) = N'{"person":{"info":{"name":"John", "name":"Jack"}}}'  
  
SELECT value FROM OPENJSON(@json, '$.person.info')  
```  
  
## Voir aussi  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)  
  
  