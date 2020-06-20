---
title: Colonnes contenant une valeur NULL par défaut | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: rothja
ms.author: jroth
ms.openlocfilehash: c08aa85254dcbd8aad0ea95edf5daac3ba9380c0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059525"
---
# <a name="columns-that-contain-a-null-value-by-default"></a>Colonnes contenant une valeur NULL par défaut
  Par défaut, une valeur NULL dans une colonne correspond à l'absence de l'attribut, du nœud ou de l'élément. Vous pouvez remplacer ce comportement par défaut en demandant un document XML centré sur l'élément à l'aide de la directive ELEMENTS et en spécifiant XSINIL afin de demander l'ajout d'éléments pour les valeurs NULL, comme le montre la requête suivante :  
  
```  
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 Le résultat est le suivant. Si XSINIL n'est pas spécifié, l'élément <`Middle`> est absent.  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode PATH avec FOR XML](use-path-mode-with-for-xml.md)  
  
  
