---
title: Filtrage des enregistrements mis à jour | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- filtering for updated records [ADO]
ms.assetid: 4a798921-d7bb-47c9-a252-550fd9463ec9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0b5afe84664719da5a1dbc7777aef524be28c459
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925336"
---
# <a name="filtering-for-updated-records"></a>Filtrage des enregistrements mis à jour
Avant d’appeler UpdateBatch, vous pouvez utiliser la propriété de filtre Recordset pour afficher uniquement les enregistrements qui ont été modifiés depuis l’ouverture du recordset ou le dernier appel à UpdateBatch. Pour ce faire, définissez le filtre sur adFilterPendingRecords pour déterminer le nombre d’enregistrements qui seront mis à jour, comme indiqué dans l’exemple de code de la section suivante.  
  
## <a name="remarks"></a>Notes  
 Cet exemple étend l’exemple UpdateBatch précédent en filtrant l’objet Recordset juste avant d’appeler la méthode UpdateBatch, en indiquant à l’utilisateur les enregistrements qui seront modifiés et en lui permettant d’annuler la mise à jour (à l’aide de la méthode CancelBatch).  
  
```  
'BeginFilterPend  
    '...  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
  
    ' Change value of Phone field for first record in Recordset, saving value  
    ' for later restoration.  
    intId = objRs1("ShipperId")  
    sPhone = objRs1("Phone")  
  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Add two new records  
    For i = 0 To 1  
        objRs1.AddNew  
        objRs1(1) = "New Shipper #" & CStr((i + 1))  
        objRs1(2) = "(nnn) 555-" & i & i & i & i  
    Next i  
  
    objRs1.Filter = adFilterPendingRecords  
  
    MsgBox "There are " & objRs1.RecordCount & " records pending.", _  
            , "Filter Pending"  
  
    ' Cancel the updates  
    objRs1.CancelBatch  
'EndFilterPend  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Mode Lot](../../../ado/guide/data/batch-mode.md)
