---
title: "Filtrage des enregistrements mis à jour | Documents Microsoft"
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
helpviewer_keywords: filtering for updated records [ADO]
ms.assetid: 4a798921-d7bb-47c9-a252-550fd9463ec9
caps.latest.revision: "4"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 37ad79ea1018a2e272cb9071bde61176ddf6348e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="filtering-for-updated-records"></a>Filtrage des enregistrements mis à jour
Avant d’invoquer UpdateBatch, vous pouvez utiliser la propriété de filtre de jeu d’enregistrements à afficher uniquement les enregistrements qui ont été modifiés depuis le jeu d’enregistrements a été ouvert ou le dernier appel à la méthode UpdateBatch. Pour ce faire, définissez Filter sur adFilterPendingRecords pour déterminer le nombre d’enregistrements sera mise à jour, comme illustré dans l’exemple de code dans la section suivante.  
  
## <a name="remarks"></a>Notes   
 Cet exemple étend l’exemple UpdateBatch précédent en filtrant le jeu d’enregistrements juste avant d’appeler la méthode UpdateBatch, montrant les enregistrements seront modifiés à l’utilisateur lui permettant d’annuler la mise à jour (à l’aide de la méthode CancelBatch).  
  
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
 [Mode batch](../../../ado/guide/data/batch-mode.md)
