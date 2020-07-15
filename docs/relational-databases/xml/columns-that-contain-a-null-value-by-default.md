---
title: Colonnes contenant une valeur NULL par défaut | Microsoft Docs
description: Apprenez à utiliser les colonnes qui contiennent une valeur NULL par défaut à l’aide de l’expression de mot clé ELEMENTs XSINIL dans SQL.
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
ms.openlocfilehash: d6962f6117a857ed5875d503c259b4d54e8dd84d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775604"
---
# <a name="columns-that-contain-a-null-value-by-default"></a>Colonnes contenant une valeur NULL par défaut

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

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
  
  
