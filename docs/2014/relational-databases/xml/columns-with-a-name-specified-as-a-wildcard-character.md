---
title: Colonnes avec un nom spécifié sous la forme d’un caractère générique | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4ff6bcd9379e6e20351dacee75cb92e56b79d374
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056149"
---
# <a name="columns-with-a-name-specified-as-a-wildcard-character"></a>Colonnes avec un nom spécifié sous la forme d'un caractère générique
  Si le nom de colonne spécifié est un caractère générique (\*), le contenu de la colonne concernée est inséré comme si aucun nom de colonne n’était spécifié. Si cette colonne est non -`xml` colonne de type, le contenu de la colonne est inséré comme un nœud de texte, comme illustré dans l’exemple suivant :  
  
```  
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
  
 `<row EmpID="1">KenJSánchez</row>`  
  
 Si la colonne est de type `xml`, l'arborescence XML correspondante est insérée. Par exemple, la requête suivante spécifie « * » pour le nom de la colonne qui contient le document XML renvoyé par la requête XQuery portant sur la colonne Instructions.  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
GO  
```  
  
 Voici l'ensemble de résultats. le document XML renvoyé par la requête XQuery est inséré sans élément d'habillage.  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location LocationID="10">...</MI:Location>`  
  
 `<MI:Location LocationID="20">...</MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode PATH avec FOR XML](use-path-mode-with-for-xml.md)  
  
  
