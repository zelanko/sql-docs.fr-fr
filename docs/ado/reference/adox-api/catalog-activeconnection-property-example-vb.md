---
title: Exemple de propriété ActiveConnection de Catalog (VB) | Microsoft Docs
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
- ActiveConnection property [ADOX], Visual Basic example
ms.assetid: bb3274b1-764d-43a7-a49f-ef55680ecd26
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4c6d30aeeb650525873669ccd175155c7e69cd0b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67967118"
---
# <a name="catalog-activeconnection-property-example-vb"></a>Exemple de propriété ActiveConnection de l’objet Catalog (VB)
La définition de la propriété [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) sur une connexion ouverte valide « ouvre » le catalogue. À partir d’un catalogue ouvert, vous pouvez accéder aux objets de schéma contenus dans ce catalogue.  
  
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
  
 Si vous définissez la propriété **ActiveConnection** sur une chaîne de connexion valide, le catalogue est également « ouvert ».  
  
```  
Attribute VB_Name = "Catalog"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, propriété (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Table, objet (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Tables, collection (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Type, propriété (table) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)
