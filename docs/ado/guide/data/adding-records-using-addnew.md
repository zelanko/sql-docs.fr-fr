---
title: Ajout d’enregistrements à l’aide de AddNew | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: cab4adff-f22f-4fb1-9217-f8138c795268
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0be4014809500c4d83b2019dc16bd083b8ed6452
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701192"
---
# <a name="adding-records-using-addnew-method"></a>Ajout d’enregistrements à l’aide de AddNew (méthode)
Voici la syntaxe de base de la **AddNew** méthode :

 *recordset*.AddNew *FieldList*, *Values*

 Le *FieldList* et *valeurs* arguments sont facultatifs. *Liste de champs* est un nom unique ou un tableau de noms ou les positions ordinales des champs dans le nouvel enregistrement.

 Le *valeurs* argument est une valeur unique ou un tableau de valeurs pour les champs dans le nouvel enregistrement.

 En règle générale, lorsque vous envisagez d’ajouter un enregistrement unique, vous appellerez la **AddNew** méthode sans aucun argument. Plus précisément, vous appellerez **AddNew**; définissez le **valeur** de chaque champ dans le nouvel enregistrement ; puis appelez **mise à jour** ou **UpdateBatch**, ou les deux. Vous pouvez vous assurer que votre **Recordset** prend en charge l’ajout de nouveaux enregistrements à l’aide de la **prend en charge** propriété avec le **adAddNew** constante énumérée.

 Le code suivant utilise cette technique pour ajouter un nouvel expéditeur à l’exemple **Recordset**. SQL Server fournit la valeur du champ n° messager automatiquement. Par conséquent, le code ne tente pas de fournir une valeur de champ pour les nouveaux enregistrements.

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
 Étant donné que ce code utilise un déconnecté **Recordset** avec un curseur côté client en mode batch, vous devez reconnecter le **Recordset** à la source de données avec un nouveau **connexion** objet avant de pouvoir appeler le **UpdateBatch** méthode pour valider les modifications apportées à la base de données. Ceci se fait facilement à l’aide de la nouvelle fonction **GetNewConnection**.
