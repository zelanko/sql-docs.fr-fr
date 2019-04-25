---
title: Paramètres de l’objet de commande | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Command object [ADO], parameters
ms.assetid: 10e7ef4a-78bf-4e91-931e-cbc6c065dd4c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f4fb4128333f1fdc5865186a202188fc64b6109f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472728"
---
# <a name="command-object-parameters"></a>Paramètres de l’objet Command
La rubrique précédente abordée [création et exécution d’une commande Simple](../../../ado/guide/data/creating-and-executing-a-simple-command.md). Une utilisation plus intéressante pour les [commande](../../../ado/reference/ado-api/command-object-ado.md) objet est indiqué dans l’exemple suivant, dans lequel la commande SQL a été paramétrée. Cette modification rend possible la réutilisation de la commande, en passant une valeur différente pour le paramètre chaque fois. Étant donné que le [propriété préparé](../../../ado/reference/ado-api/prepared-property-ado.md) propriété sur le **commande** objet est défini sur **true**, ADO nécessitera le fournisseur compiler la commande spécifiée dans [ CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) avant l’exécution pour la première fois. Il sera également conserver la commande compilée en mémoire. Cela ralentit l’exécution de la commande légèrement la première fois qu’elle est exécutée en raison de la surcharge requise pour préparer, mais entraîne un gain de performances chaque fois que la commande est appelée par la suite. Par conséquent, les commandes doivent être préparés uniquement si elles sont utilisées plusieurs fois.  
  
```  
'BeginManualParamCmd  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim objCmd As New ADODB.Command  
    Dim objParm1 As New ADODB.Parameter  
    Dim objRs As New ADODB.Recordset  
  
    ' Set the CommandText as a parameterized SQL query.  
    objCmd.CommandText = "SELECT OrderID, OrderDate, " & _  
                         "RequiredDate, ShippedDate " & _  
                         "FROM Orders " & _  
                         "WHERE CustomerID = ? " & _  
                         "ORDER BY OrderID"  
    objCmd.CommandType = adCmdText  
  
    ' Prepare command because we will be executing it more than once.  
    objCmd.Prepared = True  
  
    ' Create new parameter for CustomerID. Initial value is ALFKI.  
    Set objParm1 = objCmd.CreateParameter("CustId", adChar, _  
                    adParamInput, 5, "ALFKI")  
    objCmd.Parameters.Append objParm1  
  
    ' Connect to the data source.  
    Set objConn = GetNewConnection  
    objCmd.ActiveConnection = objConn  
  
    ' Execute once and display.  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    ' .Set new param value, re-execute command, and display.  
    objCmd("CustId") = "CACTU"  
    Set objRs = objCmd.Execute  
  
    Debug.Print objParm1.Value  
    Do While Not objRs.EOF  
        Debug.Print vbTab & objRs(0) & vbTab & objRs(1) & vbTab & _  
                    objRs(2) & vbTab & objRs(3)  
        objRs.MoveNext  
    Loop  
  
    'clean up  
    objRs.Close  
    objConn.Close  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
    Exit Sub  
  
ErrHandler:  
    'clean up  
    If objRs.State = adStateOpen Then  
        objRs.Close  
    End If  
  
    If objConn.State = adStateOpen Then  
        objConn.Close  
    End If  
  
    Set objRs = Nothing  
    Set objConn = Nothing  
    Set objCmd = Nothing  
    Set objParm1 = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
'EndManualParamCmd  
  
'BeginNewConnection  
Private Function GetNewConnection() As ADODB.Connection  
    Dim oCn As New ADODB.Connection  
    Dim sCnStr As String  
  
    sCnStr = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Integrated Security='SSPI';Initial Catalog='Northwind';"  
    oCn.Open sCnStr  
  
    If oCn.State = adStateOpen Then  
        Set GetNewConnection = oCn  
    End If  
  
End Function  
'EndNewConnection  
```  
  
 Tous les fournisseurs prennent en charge les commandes préparées. Si le fournisseur ne prend pas en charge la préparation de la commande, il peut retourner une erreur dès que cette propriété est définie sur **True**. Si elle ne retourne pas d’erreur, il ignore la demande de préparation de la commande et les affecte le **Prepared** propriété **false**.
