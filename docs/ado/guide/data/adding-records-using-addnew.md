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
ms.openlocfilehash: 36f6bad9a8f0d74a81d02ce64c78d7a91ddc0fa8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926280"
---
# <a name="adding-records-using-addnew-method"></a>Ajout d’enregistrements à l’aide de la méthode AddNew
Il s’agit de la syntaxe de base de la méthode **AddNew** :

 *Recordset*. *Valeurs* du *FieldList*AddNew

 Les arguments *FieldList* et *values* sont facultatifs. *FieldList* est un nom unique ou un tableau de noms ou de positions ordinales des champs dans le nouvel enregistrement.

 L’argument *valeurs* est soit une valeur unique, soit un tableau de valeurs pour les champs dans le nouvel enregistrement.

 En règle générale, lorsque vous envisagez d’ajouter un seul enregistrement, vous devez appeler la méthode **AddNew** sans aucun argument. Plus précisément, vous allez appeler **AddNew**. Définissez la **valeur** de chaque champ dans le nouvel enregistrement. puis appelez **Update** ou **UpdateBatch**, ou les deux. Vous pouvez vous assurer que votre **Recordset** prend en charge l’ajout de nouveaux enregistrements à l’aide de la propriété **supports** avec la constante énumérée **adAddNew** .

 Le code suivant utilise cette technique pour ajouter un nouvel expéditeur à l’exemple d' **objet Recordset**. SQL Server fournit automatiquement la valeur du champ ShipperID. Par conséquent, le code ne tente pas de fournir une valeur de champ pour les nouveaux enregistrements.

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
 Étant donné que ce code utilise un **jeu d’enregistrements** déconnecté avec un curseur côté client en mode batch, vous devez reconnecter le **Recordset** à la source de données avec un nouvel objet de **connexion** avant de pouvoir appeler la méthode **UpdateBatch** pour envoyer des modifications à la base de données. Pour ce faire, vous utilisez la nouvelle fonction **GetNewConnection**.
