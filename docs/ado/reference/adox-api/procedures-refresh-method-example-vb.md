---
title: Procedures, exemple de méthode Refresh (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Refresh method [ADOX], Visual Basic example
ms.assetid: 499679bd-287b-487d-bdfb-3803abffec1c
author: rothja
ms.author: jroth
ms.openlocfilehash: 162e6739a61b52922998a61c019225ef0f8d5216
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82748594"
---
# <a name="procedures-refresh-method-example-vb"></a>Procedures, exemple de méthode Refresh (VB)
Le code suivant montre comment actualiser la collection [procedures](../../../ado/reference/adox-api/procedures-collection-adox.md) d’un [catalogue](../../../ado/reference/adox-api/catalog-object-adox.md). Cela est nécessaire avant d’accéder aux objets de [procédure](../../../ado/reference/adox-api/procedure-object-adox.md) du **catalogue** .  
  
```  
' BeginProceduresRefreshVB  
Sub Main()  
    On Error GoTo ProcedureRefreshError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Catalog  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Refresh the Procedures collection  
    cat.Procedures.Refresh  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
ProcedureRefreshError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndProceduresRefreshVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Procedures, collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)
