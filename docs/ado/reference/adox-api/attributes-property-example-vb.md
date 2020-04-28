---
title: Attributes, exemple de propriété (VB) | Microsoft Docs
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
- Attributes property [ADOX], Visual Basic example
ms.assetid: c0ed8195-09af-42c8-99c7-038ecc8a5c9f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 378fecc379febf3daa6e17ebb2ccad748c40989f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67967138"
---
# <a name="attributes-property-example-vb"></a>Attributes, exemple de propriété (VB)
Cet exemple illustre la propriété [attributes](../../../ado/reference/adox-api/attributes-property-adox.md) d’une [colonne](../../../ado/reference/adox-api/column-object-adox.md). Sa définition sur **adColNullable** permet à l’utilisateur de définir la valeur d’un [champ](../../../ado/reference/ado-api/field-object.md) du [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sur une chaîne vide. Dans ce cas, l’utilisateur peut faire la distinction entre un enregistrement où les données ne sont pas connues et un enregistrement où les données ne s’appliquent pas.  
  
```  
' BeginAttributesVB  
Sub Main()  
    On Error GoTo AttributesXError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim colTemp As New ADOX.Column  
    Dim rstEmployees As New Recordset  
    Dim strMessage As String  
    Dim strInput As String  
    Dim tblEmp As ADOX.Table  
  
    ' Connect the catalog.  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';data source=" & _  
        "'Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
  
    Set tblEmp = cat.Tables("Employees")  
  
    ' Create a new Field object and append it to the Fields  
    ' collection of the Employees table.  
    colTemp.Name = "FaxPhone"  
    colTemp.Type = adVarWChar  
    colTemp.DefinedSize = 24  
    colTemp.Attributes = adColNullable  
    cat.Tables("Employees").Columns.Append colTemp.Name, adWChar, 24  
  
    ' Open the Employees table for updating as a Recordset  
    rstEmployees.Open "Employees", cnn, adOpenKeyset, adLockOptimistic, adCmdTable  
  
    With rstEmployees  
        ' Get user input.  
        strMessage = "Enter fax number for " & _  
            !FirstName & " " & !LastName & "." & vbCr & _  
            "[? - unknown, X - has no fax]"  
        strInput = UCase(InputBox(strMessage))  
        If strInput <> "" Then  
            Select Case strInput  
                Case "?"  
                    !FaxPhone = Null  
                Case "X"  
                    !FaxPhone = ""  
                Case Else  
                    !FaxPhone = strInput  
            End Select  
            .Update  
  
            ' Print report.  
            Debug.Print "Name - Fax number"  
            Debug.Print !FirstName & " " & !LastName & " - ";  
  
            If IsNull(!FaxPhone) Then  
                Debug.Print "[Unknown]"  
            Else  
                If !FaxPhone = "" Then  
                    Debug.Print "[Has no fax]"  
                Else  
                    Debug.Print !FaxPhone  
                End If  
            End If  
  
        End If  
  
        .Close  
    End With  
  
    'Clean up  
    tblEmp.Columns.Delete colTemp.Name  
    cnn.Close  
    Set rstEmployees = Nothing  
    Set cat = Nothing  
    Set colTemp = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
AttributesXError:  
  
    If Not rstEmployees Is Nothing Then  
        If rstEmployees.State = adStateOpen Then rstEmployees.Close  
    End If  
    Set rstEmployees = Nothing  
  
    If Not tblEmp Is Nothing Then tblEmp.Columns.Delete colTemp.Name  
  
    Set cat = Nothing  
    Set colTemp = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
' EndAttributesVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Attributes, propriété (ADOX)](../../../ado/reference/adox-api/attributes-property-adox.md)   
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Column, objet (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
