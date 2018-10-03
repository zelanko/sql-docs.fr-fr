---
title: La mise en forme | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- reshaping previously shaped Recordset [ADO]
- data shaping [ADO], reshaping
ms.assetid: b1c965b7-3dad-4de6-9e0e-502ca8785be3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 324801cbfc97db4e2a1137fa04df0c74dc1897a1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47714527"
---
# <a name="reshaping"></a>Remise en forme
Un **Recordset** créé par une clause d’une forme commande peut-être être affectée un *alias* nom (généralement avec le mot clé AS). L’alias d’une forme **Recordset** peut être référencée dans une commande totalement différente. Autrement dit, vous pouvez réutiliser ou *remodeler*, un préalablement mis en forme **Recordset** dans une nouvelle commande de forme. Pour prendre en charge cette fonctionnalité, ADO fournit une propriété, [Reshape Name](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md).  
  
 La mise en forme a deux fonctions principales. La première consiste à associer un existant **Recordset** avec un nouveau parent **Recordset**.  
  
## <a name="example"></a>Exemple  
  
```  
rs1.Open "SHAPE {select * from Customers} " & _  
         "APPEND ({select * from Orders} AS chapOrders " & _  
         "RELATE CustomerID to CustomerID)", cn  
  
rs2.Open "SHAPE {select * from Employees} " & _  
         "APPEND (chapOrders RELATE EmployeeID to EmployeeID)", cn  
```  
  
 La deuxième fonction consiste à activer l’accès à chapitre à enfant existant **Recordset** objets, à l’aide de la syntaxe « forme \<recordset remodeler nom > ».  
  
> [!NOTE]
>  Impossible d’ajouter des colonnes à une **Recordset**, remodeler un paramétrable **Recordset** ou **Recordset** des objets d’une clause COMPUTE intermédiaire, ou effectuer agréger des opérations sur n’importe quel **Recordset** descendants à partir de la **Recordset** en cours reformé. Le **Recordset** en cours reformé et la nouvelle forme de commande doivent tous deux utiliser le même [connexion](../../../ado/reference/ado-api/connection-object-ado.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)
