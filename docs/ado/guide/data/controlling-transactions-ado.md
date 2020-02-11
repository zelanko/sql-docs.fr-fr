---
title: Contrôle des transactions (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- transactions [ADO]
ms.assetid: 189240e8-3ffa-4024-81a9-c6cb5d17eee0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3a8a13ee7637c0cb16e33e626a218e28242dabf4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925776"
---
# <a name="controlling-transactions-ado"></a>Contrôle des transactions (ADO)
ADO prend en charge le traitement des transactions dans une connexion à l’aide des méthodes **BeginTrans**, **CommitTrans**et **RollbackTrans** sur un objet **Connection** . L’idée générale de l’implémentation du traitement des transactions dans ADO est illustrée dans l’extrait de code simple suivant.  
  
```  
Const DS = "MySqlServer"  
Const DB = "Northwind"  
Const DP = "SQLOLEDB"  
  
Dim oConn As ADODB.Connection  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
  
sConn = "Provider=" & DP & _  
          ";Data Source=" & DS & _  
          ";Initial Catalog=" & DB & _  
          ";Integrated Security=SSPI;"  
  
sSQL = "SELECT ProductID, ProductName FROM Products"  
  
Set oConn = New ADODB.Connection  
oConn.Open sConn  
  
' Create and Open the Recordset object.  
Set oRs = New ADODB.Recordset  
oRs.Open sSQL, oConn, adOpenStatic, adLockOptimistic, adCmdText  
  
If oRs.RecordCount > 1 Then  
  
    oRs.MoveFirst  
    Id1 = oRs("ProductID")  
    Name1 = oRs("ProductName")  
    oRs.MoveNext  
    Id2 = oRs("ProductID")  
    Name2 = oRs("ProductName")  
  
    q = "Switch ID's of " & Name1 & " and " & Name2 & "?"  
    If MsgBox(q, vbYesNo) = vbYes Then  
        oRs.MoveFirst  
        oRs("ProductName") = Name2  
        oRs.Update  
  
        oRs.MoveNext  
        oRs("ProductName") = Name1  
        oRs.Update  
  
        If MsgBox("Save changes?", vbYesNo) = vbYes Then  
  
        Else  
  
        End If  
    End If  
  
End If  
  
oRs.Close  
oConn.Close  
```  
  
 Ici, le traitement des transactions permet de s’assurer que les deux enregistrements sont mis à jour comme une unité d’exploitation et que les deux noms de produits sont interchangeables ou inchangés du tout.  
  
 Pour obtenir des informations détaillées sur le traitement des transactions [, consultez Mise à jour et persistance des données](../../../ado/guide/data/updating-and-persisting-data.md).
