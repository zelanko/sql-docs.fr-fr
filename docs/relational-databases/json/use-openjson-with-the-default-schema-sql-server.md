---
title: "Utiliser OPENJSON avec le sch&#233;ma par d&#233;faut (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OPENJSON, avec le schéma par défaut"
ms.assetid: 8e28a8f8-71a8-4c25-96b8-0bbedc6f41c4
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Utiliser OPENJSON avec le sch&#233;ma par d&#233;faut (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  L’utilisation de **OPENJSON** avec le schéma par défaut permet de retourner une table comprenant une ligne pour chaque propriété de l’objet ou pour chaque élément du tableau.  
  
 Voici quelques exemples d’utilisation de **OPENJSON** avec le schéma par défaut. Pour en savoir plus et obtenir d’autres exemples, consultez [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
## Exemple : retourner chaque propriété d’un objet  
 **Requête**  
  
```tsql  
SELECT * FROM OPENJSON('{"name":"John","surname":"Doe","age":45}')  
```  
  
 **Résultats**  
  
|Clé|Valeur|  
|---------|-----------|  
|name|John|  
|surname|Doe|  
|age|45|  
  
## Exemple : retourner chaque élément d’un tableau  
 **Requête**  
  
```tsql  
SELECT [key], value FROM OPENJSON('["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]')  
```  
  
 **Résultats**  
  
|Clé|Valeur|  
|---------|-----------|  
|0|en-GB|  
|1|en-UK|  
|2|de-AT|  
|3|es-AR|  
|4|sr-Cyrl|  
  
## Exemple : convertir des données JSON en table temporaire  
 La requête suivante retourne toutes les propriétés de l’objet **info** .  
  
```tsql  
SET @json = N'{  
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
  
SELECT * FROM OPENJSON(@json, N'lax $.info')  
```  
  
 **Résultats**  
  
|Clé|Valeur|Type|  
|---------|-----------|----------|  
|type|1|0|  
|address|{ "town":"Bristol", "county":"Avon", "country":"England" }|5|  
|tags|[ "Sport", "Water polo" ]|4|  
  
## Exemple : combiner des données relationnelles et des données JSON  
 Dans l’exemple suivant, la table SalesOrderHeader a une colonne de texte SalesReason qui contient un tableau d’objets SalesOrderReasons au format JSON. Les objets SalesOrderReasons contiennent des propriétés telles que « Manufacturer » (Fabricant) et « Quality » (Qualité). L’exemple crée un rapport qui relie chaque ligne de commande client au motif de vente associé en développant le tableau JSON de motifs de vente comme si les motifs étaient stockés dans une table enfant distincte.  
  
```tsql  
SELECT SalesOrderID, OrderDate, value AS Reason  
FROM Sales.SalesOrderHeader  
    CROSS APPLY OPENJSON (SalesReasons)  
  
```  
  
 Dans cet exemple, OPENJSON retourne une table de motifs de vente dans laquelle les motifs forment la colonne de valeurs. L’opérateur CROSS APPLY relie chaque ligne de commande client aux lignes retournées par la fonction table OPENJSON.  
  
## Voir aussi  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  