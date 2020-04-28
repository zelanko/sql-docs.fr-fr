---
title: Utilisation d’un objet Recordset | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 01c630d8-eb35-4bd0-a99f-7c0f85316cc1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dda89464598ddc4ecfee0078b36aadd01b4486f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923633"
---
# <a name="using-a-recordset-object"></a>Utilisation d’un objet Recordset
Vous pouvez également utiliser **Recordset. Open** pour établir implicitement une connexion et émettre une commande sur cette connexion en une seule opération. Par exemple, dans Visual Basic :  
  
```  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
  
' Create and Open the Recordset object.  
Set oRs = New ADODB.Recordset  
oRs.CursorLocation = adUseClient  
oRs.Open sSQL, sConn, adOpenStatic, _  
               adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
oRs.Close          
Set oRs = Nothing  
```  
  
 Notez que **ors. Open** prend une chaîne de connexion (*sConn*), à la place d’un objet de **connexion** (*oConn*), en tant que valeur de son paramètre **ActiveConnection** . Le type de curseur côté client est également appliqué en définissant la propriété **CursorLocation** sur l’objet **Recordset** . Là encore, Comparez ceci avec l’exemple de **HelloData** .
