---
title: "Utiliser OPENJSON avec le schéma par défaut (SQL Server) | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: OPENJSON, with default schema
ms.assetid: 8e28a8f8-71a8-4c25-96b8-0bbedc6f41c4
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 035a4b887638f64ddc1d7ee4aef0aaa81958047f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="use-openjson-with-the-default-schema-sql-server"></a>Utiliser OPENJSON avec le schéma par défaut (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  L’utilisation de **OPENJSON** avec le schéma par défaut permet de retourner une table comprenant une ligne pour chaque propriété de l’objet ou pour chaque élément du tableau.  
  
 Voici quelques exemples d’utilisation de **OPENJSON** avec le schéma par défaut. Pour en savoir plus et obtenir d’autres exemples, consultez [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
## <a name="example---return-each-property-of-an-object"></a>Exemple : retourner chaque propriété d’un objet  
 **Requête**  
  
```sql  
SELECT *
FROM OPENJSON('{"name":"John","surname":"Doe","age":45}') 
```  
  
 **Résultats**  
  
|Clé|Valeur|  
|---------|-----------|  
|name|John|  
|surname|Doe|  
|age|45|  
  
## <a name="example---return-each-element-of-an-array"></a>Exemple : retourner chaque élément d’un tableau  
 **Requête**  
  
```sql  
SELECT [key],value
FROM OPENJSON('["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]') 
```  
  
 **Résultats**  
  
|Clé|Valeur|  
|---------|-----------|  
|0|en-GB|  
|1|en-UK|  
|2|de-AT|  
|3|es-AR|  
|4|sr-Cyrl|  
  
## <a name="example---convert-json-to-a-temporary-table"></a>Exemple : convertir des données JSON en table temporaire  
 La requête suivante retourne toutes les propriétés de l’objet **info** .  
  
```sql  
DECLARE @json NVARCHAR(MAX)

SET @json=N'{  
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

SELECT *
FROM OPENJSON(@json,N'lax $.info')
```  
  
 **Résultats**  
  
|Clé|Valeur|Type|  
|---------|-----------|----------|  
|Type|1|0|  
|address|{ "town":"Bristol", "county":"Avon", "country":"England" }|5|  
|tags|[ "Sport", "Water polo" ]|4|  
  
## <a name="example---combine-relational-data-and-json-data"></a>Exemple : combiner des données relationnelles et des données JSON  
 Dans l’exemple suivant, la table SalesOrderHeader a une colonne de texte SalesReason qui contient un tableau d’objets SalesOrderReasons au format JSON. Les objets SalesOrderReasons contiennent des propriétés telles que « Manufacturer » (Fabricant) et « Quality » (Qualité). L’exemple crée un rapport qui relie chaque ligne de commande client au motif de vente associé en développant le tableau JSON de motifs de vente comme si les motifs étaient stockés dans une table enfant distincte.  
  
```sql  
SELECT SalesOrderID,OrderDate,value AS Reason
FROM Sales.SalesOrderHeader
CROSS APPLY OPENJSON(SalesReasons)
```  
  
 Dans cet exemple, OPENJSON retourne une table de motifs de vente dans laquelle les motifs forment la colonne de valeurs. L’opérateur CROSS APPLY relie chaque ligne de commande client aux lignes retournées par la fonction table OPENJSON.  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la prise en charge intégrée de JSON dans SQL Server  
Pour accéder à un grand nombre de solutions spécifiques, de cas d’usage et de recommandations, consultez les [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et Azure SQL Database, écrits par Jovan Popovic (Microsoft Program Manager).
  
## <a name="see-also"></a>Voir aussi  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  
