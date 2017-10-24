---
title: "Envoyer les mises à jour : méthode UpdateBatch | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87123797-831f-48e0-94b5-f669f9ca194a
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6cad1bfd63ffafd32d0621f6142717cd7175ccd0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sending-the-updates-updatebatch-method"></a>Envoyer les mises à jour : méthode UpdateBatch
Le code suivant ouvre un objet Recordset en mode batch en affectant la propriété LockType adLockBatchOptimistic et CursorLocation adUseClient. Il ajoute deux nouveaux enregistrements et modifie la valeur d’un champ dans un enregistrement existant, en enregistrant les valeurs d’origine, puis appelle la méthode UpdateBatch pour renvoyer les modifications à la source de données.  
  
## <a name="remarks"></a>Notes  
  
```  
'BeginBatchUpdate  
    strConn = "Provider=SQLOLEDB;Initial Catalog=Northwind;" & _  
              "Data Source=MySQLServer;Integrated Security=SSPI;"  
  
    strSQL = "SELECT ShipperId, CompanyName, Phone FROM Shippers"  
  
    Set objRs1 = New ADODB.Recordset  
    objRs1.CursorLocation = adUseClient  
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
  
    ' Send the updates  
    objRs1.UpdateBatch  
'EndBatchUpdate  
```  
  
 Si vous modifiez l’enregistrement actif ou ajouter un nouvel enregistrement lorsque vous appelez la méthode UpdateBatch, ADO appelle automatiquement la méthode de mise à jour pour enregistrer les modifications en attente à l’enregistrement actif avant de transmettre les modifications par lot au fournisseur.  
  
## <a name="see-also"></a>Voir aussi  
 [En Mode Batch](../../../ado/guide/data/batch-mode.md)

