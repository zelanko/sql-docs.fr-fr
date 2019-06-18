---
title: Colonnes avec un nom spécifié sous la forme d’un caractère générique | Microsoft Docs
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 261c58fd5849ea47109643ce80f4420e01ebe7f9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66175320"
---
# <a name="columns-with-a-name-specified-as-a-wildcard-character"></a>Colonnes avec un nom spécifié sous la forme d'un caractère générique

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Si le nom de colonne spécifié est un caractère générique (\*), le contenu de la colonne concernée est inséré comme si aucun nom de colonne n’était spécifié. Si cette colonne est une colonne de type non-**xml** , le contenu de la colonne est inséré en tant que nœud de texte, comme le montre l’exemple suivant :  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
       FirstName "*",   
       MiddleName "*",   
       LastName "*"  
FROM   HumanResources.Employee AS E  
  INNER JOIN Person.Person AS P  
    ON E.BusinessEntityID = P.BusinessEntityID  
WHERE E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 Voici le résultat obtenu :  

```xml
<row EmpID="1">KenJSánchez</row>
```

 Si la colonne est de type **xml** , l’arborescence XML correspondante est insérée. Par exemple, la requête suivante spécifie « * » pour le nom de la colonne qui contient le document XML renvoyé par la requête XQuery portant sur la colonne Instructions.  
  
```sql
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
```  
  
 Voici l'ensemble de résultats. le document XML renvoyé par la requête XQuery est inséré sans élément d'habillage.  

```xml
<row>
  <ProductModelID>7</ProductModelID>
  <Name>HL Touring Frame</Name>
  <MI:Location LocationID="10">...</MI:Location>
  <MI:Location LocationID="20">...</MI:Location>
  ...
</row>
```

## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode PATH avec FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
