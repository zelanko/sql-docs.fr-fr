---
title: "Ajout d’enregistrements à l’aide de AddNew | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: cab4adff-f22f-4fb1-9217-f8138c795268
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 92bbc404985ebbb49c4e654efd5a7f54198d35ab
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="adding-records-using-addnew-method"></a>Ajout d’enregistrements à l’aide de AddNew (méthode)
Voici la syntaxe de base de la **AddNew** méthode :

 *jeu d’enregistrements*. AddNew *liste de champs*, *valeurs*

 Le *liste de champs* et *valeurs* arguments sont facultatifs. *Liste de champs* est un nom unique ou un tableau de noms ou de positions ordinales des champs dans le nouvel enregistrement.

 Le *valeurs* argument est une valeur unique ou un tableau de valeurs pour les champs dans le nouvel enregistrement.

 En règle générale, lorsque vous envisagez d’ajouter un enregistrement unique, vous appellerez la **AddNew** méthode sans arguments. Plus précisément, vous appellerez **AddNew**; définissez la **valeur** de chaque champ dans le nouvel enregistrement ; puis appelez **mise à jour** ou **UpdateBatch**, ou les deux. Vous pouvez vous assurer que votre **Recordset** prend en charge l’ajout de nouveaux enregistrements à l’aide de la **prend en charge** propriété avec le **adAddNew** constante énumérée.

 Le code suivant utilise cette technique pour ajouter un nouvel expéditeur à l’exemple **Recordset**. SQL Server fournit la valeur du champ ShipperID automatiquement. Par conséquent, le code ne tente pas de fournir une valeur de champ pour les nouveaux enregistrements.

```
'BeginAddNew1.1
If objRs.Supports(adAddNew) Then
    With objRs
        .AddNew
        .Fields("CompanyName") = "Sample Shipper"
        .Fields("Phone") = "(931) 555-6334"
        .Update
    End With
End If
'EndAddNew1.1
```

## <a name="remarks"></a>Notes
 Étant donné que ce code utilise un déconnecté **Recordset** avec un curseur côté client en mode batch, vous devez reconnecter le **Recordset** à la source de données avec un nouveau **connexion** l’objet avant de pouvoir appeler le **UpdateBatch** méthode pour valider les modifications apportées à la base de données. Cela est facilement effectué à l’aide de la nouvelle fonction **GetNewConnection**.

