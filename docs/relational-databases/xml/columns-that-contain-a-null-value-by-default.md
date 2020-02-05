---
title: Colonnes contenant une valeur NULL par défaut | Microsoft Docs
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0fb8b86daedb73f62396e1dc13a06a5a4e2a7bb3
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68113074"
---
# <a name="columns-that-contain-a-null-value-by-default"></a>Colonnes contenant une valeur NULL par défaut

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Par défaut, une valeur NULL dans une colonne correspond à l'absence de l'attribut, du nœud ou de l'élément. Ce comportement par défaut peut être substitué à l’aide de l’expression de mot clé ELEMENTS XSINIL. Cette expression demande du XML centré sur des éléments. Cela signifie que les valeurs Null sont explicitement indiquées dans les résultats retournés. Ces éléments n’ont aucune valeur.

L’expression ELEMENTS XSINIL est illustrée dans l’exemple Transact-SQL SELECT suivant.

```sql
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
  AND  E.EmployeeID=1
FOR XML PATH, ELEMENTS XSINIL;
```  
  
 Le résultat est le suivant. Si XSINIL n'est pas spécifié, l'élément <`Middle`> est absent.  
  
```xml
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode PATH avec FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
