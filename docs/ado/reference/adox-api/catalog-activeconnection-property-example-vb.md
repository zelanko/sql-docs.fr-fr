---
title: "Exemple de propriété ActiveConnection (VB) de catalogue | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ActiveConnection property [ADOX], Visual Basic example
ms.assetid: bb3274b1-764d-43a7-a49f-ef55680ecd26
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 382c25c68f911a48095593879a2657ac5409fc89
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-activeconnection-property-example-vb"></a>Exemple de propriété ActiveConnection catalogue (VB)
Définition de la [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) propriété à une connexion valide, ouvrez « ouvre » le catalogue. À partir d’un catalogue ouvert, vous pouvez accéder les objets de schéma contenus dans ce catalogue.  
  
```  
' BeginOpenConnectionVB  
Sub Main()  
    On Error GoTo OpenConnectionError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source= 'Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
    Debug.Print cat.Tables(0).Type  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
OpenConnectionError:  
  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndOpenConnectionVB  
```  
  
 Définition de la **ActiveConnection** propriété dans une chaîne de connexion valide « ouvre également « du catalogue.  
  
```  
Attribute VB_Name = "Catalog"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, propriété (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Objet catalogue (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Objet table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Collection de tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Type, propriété (Table) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)
