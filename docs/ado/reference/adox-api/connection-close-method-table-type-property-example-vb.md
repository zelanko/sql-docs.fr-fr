---
title: Connexion Close, méthode, exemple de propriété de Type de Table (VB) | Microsoft Docs
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
- Close method [ADOX], Visual Basic example
- Type property [ADOX], Visual Basic example
ms.assetid: f88e7a3b-19ed-46e2-b2ce-3b611d9b8166
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: aa4089925e5a51f5e4fa4578094634e724b8a615
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703374"
---
# <a name="connection-close-method-table-type-property-example-vb"></a>Close, méthode de l’objet Connection, Type (exemple de propriété de l’objet Table) (VB)
Définition de la [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) propriété **rien** doit fermer la connexion au catalogue. Regroupements associés sera vides. Tous les objets qui ont été créés à partir des objets de schéma dans le catalogue sont orphelins. Toutes les propriétés sur les objets qui ont été mis en cache seront toujours disponibles, mais une tentative de lecture des propriétés qui nécessite un appel au fournisseur échouera.  
  
```  
' BeginCloseConnectionVB  
Sub Main()  
    On Error GoTo CloseConnectionByNothingError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim tbl As ADOX.Table  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source= 'Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
    Set tbl = cat.Tables(0)  
    Debug.Print tbl.Type    ' Cache tbl.Type info  
    Set cat.ActiveConnection = Nothing  
    Debug.Print tbl.Type    ' tbl is orphaned  
    ' Previous line will succeed if this info was cached.  
    Debug.Print tbl.Columns(0).DefinedSize  
    ' Previous line will fail if this info has not been cached.  
  
    'Clean up.  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
CloseConnectionByNothingError:  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCloseConnectionVB  
```  
  
 Fermeture d’un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet qui a été utilisée pour ouvrir le catalogue doit avoir le même effet que le paramètre le **ActiveConnection** propriété **rien**.  
  
```  
Attribute VB_Name = "Connection"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, propriété (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Objet de colonne (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)   
 [Columns, Collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Table, objet (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Tables, Collection (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Type, propriété (table) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)
