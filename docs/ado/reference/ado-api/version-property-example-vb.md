---
title: "Exemple de propriété version (VB) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: VB
helpviewer_keywords: Version property [ADO], Visual Basic example
ms.assetid: 708efd50-2905-4168-b7e4-91b2e9b23539
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f810e8a89ff1284e4b73386ac3f049e89d4c0931
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="version-property-example-vb"></a>Exemple de propriété version (VB)
Cet exemple utilise le [Version](../../../ado/reference/ado-api/version-property-ado.md) propriété d’un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet pour afficher la version ADO actuelle. Il utilise aussi plusieurs propriétés dynamiques pour afficher :  
  
-   le nom du SGBD actuelle et la version.  
  
-   Version de OLE DB.  
  
-   Nom du fournisseur et la version.  
  
-   Version d’ODBC.  
  
-   Nom du pilote ODBC et la version.  
  
```  
'BeginVersionVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strVersionInfo As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    strVersionInfo = "ADO Version: " & Cnxn.Version & vbCr  
    strVersionInfo = strVersionInfo & "DBMS Name: " & Cnxn.Properties("DBMS Name") & vbCr  
    strVersionInfo = strVersionInfo & "DBMS Version: " & Cnxn.Properties("DBMS Version") & vbCr  
    strVersionInfo = strVersionInfo & "OLE DB Version: " & Cnxn.Properties("OLE DB Version") & vbCr  
    strVersionInfo = strVersionInfo & "Provider Name: " & Cnxn.Properties("Provider Name") & vbCr  
    strVersionInfo = strVersionInfo & "Provider Version: " & Cnxn.Properties("Provider Version") & vbCr  
  
    MsgBox strVersionInfo  
  
    ' clean up  
    Cnxn.Close  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndVersionVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de connexion (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Version, propriété (ADO)](../../../ado/reference/ado-api/version-property-ado.md)
