---
title: Status, exemple de propriété (objet Field) (VB) | Microsoft Docs
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
- Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c28a0b615a9f250c8539e87abf9fefbc11f513ee
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916828"
---
# <a name="status-property-example-field-vb"></a>Status, exemple de propriété (objet Field) (VB)
L’exemple suivant ouvre un document à partir d’un dossier en lecture/écriture à l’aide du [fournisseur de publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Le [état](../../../ado/reference/ado-api/status-property-ado-field.md) propriété d’un [champ](../../../ado/reference/ado-api/field-object.md) objet de la [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) sera tout d’abord être définie sur **adFieldPendingInsert**, puis de mettre à jour **adFieldOk**.  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=https://MyServer/"  
   Cnxn.Open strCnxn  
  
   Set File = New ADODB.Record  
   strFile = "Folder/FileName"  
   ' Open a read/write document  
   File.Source = strFile  
   File.ActiveConnection = Cnxn  
   File.Mode = adModeReadWrite  
   File.Open  
  
   Debug.Print "Append a couple of fields"  
  
   File.Fields.Append "chektest:fld1", adWChar, 42, adFldUpdatable, "fld1"  
   File.Fields.Append "chektest:fld2", adWChar, 42, adFldUpdatable, "fld2"  
  
   Debug.Print "status for the fields"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert  
  
    'turn off error-handling to verify field status  
   On Error Resume Next  
  
   File.Fields.Update  
  
   Debug.Print "Update succeeds"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert + adFieldUnavailable  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert + adFieldUnavailable  
  
    ' resume default error-handling  
   On Error GoTo 0  
  
     ' clean up  
    File.Close  
    Cnxn.Close  
    Set File = Nothing  
    Set Cnxn = Nothing  
  
End Sub  
'EndStatusFieldVB  
```  
  
 L’exemple suivant supprime un connu **champ** à partir d’un **enregistrement** ouvert à partir d’un document. Le **état** propriété sera tout d’abord être définie sur **adFieldOK**, puis **adFieldPendingUnknown**.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 Le code ci-dessous supprime une **champ** à partir d’un **enregistrement** ouvert sur un document en lecture seule. **État** sera défini sur **adFieldPendingDelete**. À [mise à jour](../../../ado/reference/ado-api/update-method.md), la suppression échoue et **état** sera **adFieldPendingDelete** plus **adFieldPermissionDenied**. [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) efface l’en attente **état** paramètre.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de champ](../../../ado/reference/ado-api/field-object.md)   
 [Enregistrement objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Status, propriété (objet Field ADO)](../../../ado/reference/ado-api/status-property-ado-field.md)
