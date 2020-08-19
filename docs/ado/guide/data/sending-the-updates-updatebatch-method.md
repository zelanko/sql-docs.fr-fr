---
description: 'Envoi des mises à jour : UpdateBatch, méthode'
title: 'Envoi des mises à jour : méthode UpdateBatch | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 87123797-831f-48e0-94b5-f669f9ca194a
author: rothja
ms.author: jroth
ms.openlocfilehash: 8b5378cad96bc2827badc2e15a23d7f48f683381
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452881"
---
# <a name="sending-the-updates-updatebatch-method"></a>Envoi des mises à jour : UpdateBatch, méthode
Le code suivant ouvre un Recordset en mode batch en affectant à la propriété LockType la valeur adLockBatchOptimistic et à l’option CursorLocation la valeur adUseClient. Il ajoute deux nouveaux enregistrements et modifie la valeur d’un champ dans un enregistrement existant, en enregistrant les valeurs d’origine, puis appelle UpdateBatch pour renvoyer les modifications à la source de données.  
  
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
  
 Si vous modifiez l’enregistrement en cours ou si vous ajoutez un nouvel enregistrement lorsque vous appelez la méthode UpdateBatch, ADO appelle automatiquement la méthode Update pour enregistrer toutes les modifications en attente dans l’enregistrement en cours avant de transmettre les modifications par lot au fournisseur.  
  
## <a name="see-also"></a>Voir aussi  
 [Mode Batch](../../../ado/guide/data/batch-mode.md)
