---
description: GetObjectOwner et SetObjectOwner, exemples de méthodes (VB)
title: GetObjectOwner et SetObjectOwner, exemple de méthodes (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- SetObjectOwner method [ADOX], Visual Basic example
- GetObjectOwner method [ADOX], Visual Basic example
ms.assetid: e44ec3d4-42ae-447d-aaed-bdea53cb0cca
author: rothja
ms.author: jroth
ms.openlocfilehash: 6b3033c06d7853768069b20493494e128991abff
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984570"
---
# <a name="getobjectowner-and-setobjectowner-methods-example-vb"></a>GetObjectOwner et SetObjectOwner, exemples de méthodes (VB)
Cet exemple illustre les méthodes [GetObjectOwner](./getobjectowner-method-adox.md) et [SetObjectOwner](./setobjectowner-method.md) . Ce code suppose l’existence de la gestion des groupes (voir les [groupes et les utilisateurs Append, exemple de méthodes ChangePassword (VB)](./groups-and-users-append-changepassword-methods-example-vb.md) pour voir comment ajouter ce groupe au système). Le propriétaire de la table categories est défini sur Accounting.  
  
```  
' BeginOwnersVB  
Sub OwnersX()  
  
    Dim tblLoop As New ADOX.Table  
    Dim cat As New ADOX.Catalog  
    Dim strOwner As String  
  
    ' Open the Catalog.  
    cat.ActiveConnection = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=c:\Program Files\" & _  
        "Microsoft Office\Office\Samples\Northwind.mdb;" & _  
        "jet oledb:system database=" & _  
        "c:\Program Files\Microsoft Office\Office\system.mdw"  
  
    ' Print the original owner of Categories  
    strOwner = cat.GetObjectOwner("Categories", adPermObjTable)  
    Debug.Print "Owner of Categories: " & strOwner  
  
    ' Set the owner of Categories to Accounting  
    cat.SetObjectOwner "Categories", adPermObjTable, "Accounting"  
  
    ' List the owners of all tables and columns in the catalog.  
    For Each tblLoop In cat.Tables  
        Debug.Print "Table: " & tblLoop.Name  
        Debug.Print "   Owner: " & _  
            cat.GetObjectOwner(tblLoop.Name, adPermObjTable)  
    Next tblLoop  
  
    ' Restore the original owner of Categories  
    cat.SetObjectOwner "Categories", adPermObjTable, strOwner  
  
End Sub  
' EndOwnersVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Catalog, objet (ADOX)](./catalog-object-adox.md)   
 [GetObjectOwner, méthode (ADOX)](./getobjectowner-method-adox.md)   
 [SetObjectOwner, méthode](./setobjectowner-method.md)