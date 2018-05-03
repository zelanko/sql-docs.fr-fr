---
title: Actualiser les vues, méthode-exemple (VB) | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Refresh method [ADOX]
ms.assetid: cdad2d66-6ade-40dc-9e74-e40cfa9bc127
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6a6a684dd7ea0d0be9df4fdd75a56048db6e908
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="views-refresh-method-example-vb"></a>Actualiser les vues, méthode-exemple (VB)
Le code suivant montre comment actualiser le [vues](../../../ado/reference/adox-api/views-collection-adox.md) collection d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md). Cela est nécessaire avant [vue](../../../ado/reference/adox-api/view-object-adox.md) des objets de la **catalogue** sont accessibles.  
  
```  
' BeginViewsRefreshVB  
Sub Main()  
    On Error GoTo ProcedureViewsRefreshError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the catalog.  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Refresh the Procedures collection.  
    cat.Views.Refresh  
  
    'Clean up  
    Set cat = Nothing  
    Exit Sub  
  
ProcedureViewsRefreshError:  
  
    If Not cat Is Nothing Then  
        Set cat = Nothing  
    End If  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndViewsRefreshVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [Views, collection (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
