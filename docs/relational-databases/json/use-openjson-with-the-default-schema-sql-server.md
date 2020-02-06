---
title: Utiliser OPENJSON avec le schéma par défaut
ms.date: 06/02/2016
ms.prod: sql
ms.reviewer: genemi
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- OPENJSON, with default schema
ms.assetid: 8e28a8f8-71a8-4c25-96b8-0bbedc6f41c4
author: jovanpop-msft
ms.author: jovanpop
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3e4aac74ac35fc5d75320b420e85b130be110340
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "74096037"
---
# <a name="use-openjson-with-the-default-schema-sql-server"></a>Utiliser OPENJSON avec le schéma par défaut (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

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
|type|1|0|  
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

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>En savoir plus sur JSON dans SQL Server et Azure SQL Database  
  
### <a name="microsoft-videos"></a>Vidéos Microsoft

Pour obtenir une présentation visuelle de la prise en charge intégrée de JSON dans SQL Server et Azure SQL Database, consultez les vidéos suivantes :

-   [SQL Server 2016 et prise en charge de JSON](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Utilisation de JSON dans SQL Server 2016 et Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON : un pont entre les mondes relationnel et NoSQL](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)
  
## <a name="see-also"></a>Voir aussi  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
