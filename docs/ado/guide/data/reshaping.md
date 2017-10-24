---
title: La mise en forme | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reshaping previously shaped Recordset [ADO]
- data shaping [ADO], reshaping
ms.assetid: b1c965b7-3dad-4de6-9e0e-502ca8785be3
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d5264de973e4ed36cc24eb5c535576bdfa0a7228
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="reshaping"></a>La mise en forme
A **Recordset** créé par une clause d’une forme de commande peut avoir un *alias* nom (généralement avec le mot clé AS). L’alias d’une forme **Recordset** peut être référencée dans une commande totalement différente. Autrement dit, vous pouvez réutiliser ou *remodeler*, un préalablement mis en forme **Recordset** dans une nouvelle commande de forme. Pour prendre en charge cette fonctionnalité, ADO fournit une propriété, [nom de remodeler](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md).  
  
 La mise en forme a deux fonctions principales. La première consiste à associer un existant **Recordset** avec un nouveau parent **Recordset**.  
  
## <a name="example"></a>Exemple  
  
```  
rs1.Open "SHAPE {select * from Customers} " & _  
         "APPEND ({select * from Orders} AS chapOrders " & _  
         "RELATE CustomerID to CustomerID)", cn  
  
rs2.Open "SHAPE {select * from Employees} " & _  
         "APPEND (chapOrders RELATE EmployeeID to EmployeeID)", cn  
```  
  
 La deuxième fonction consiste à activer l’accès non chapitre enfant existant **Recordset** des objets, à l’aide de la syntaxe « forme \<recordset remodeler nom > ».  
  
> [!NOTE]
>  Ne peut pas ajouter des colonnes à une **Recordset**, remodeler un paramétrable **Recordset** ou **Recordset** des objets dans une clause COMPUTE intermédiaire, ou effectuer regrouper des opérations sur n’importe quel **Recordset** descendants à partir de la **Recordset** est redessinée. Le **Recordset** en cours reformé et la nouvelle forme de commande doivent tous deux utiliser le même [connexion](../../../ado/reference/ado-api/connection-object-ado.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)

