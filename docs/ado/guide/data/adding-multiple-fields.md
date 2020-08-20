---
description: Ajout de plusieurs champs et valeurs
title: Ajout de plusieurs champs | Microsoft Docs
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
- editing data [ADO], adding multiple fields
- editing data [ADO], AddNew method
ms.assetid: f3648ef4-9f36-4991-a868-83a617389844
author: rothja
ms.author: jroth
ms.openlocfilehash: e2543741749c1521526aea18bc4600168559eb45
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453891"
---
# <a name="adding-multiple-fields-and-values"></a>Ajout de plusieurs champs et valeurs
Parfois, il peut être plus efficace de passer un tableau de champs et leurs valeurs correspondantes à la méthode **AddNew** , plutôt que de définir plusieurs fois la **valeur** pour chaque nouveau champ. Si *FieldList* est un tableau, les *valeurs* doivent également être un tableau avec le même nombre de membres ; dans le cas contraire, une erreur se produit. L’ordre des noms de champs doit correspondre à l’ordre des valeurs de champ dans chaque tableau. Le code suivant passe un tableau de champs et un tableau de valeurs à la méthode **AddNew** .

```
'BeginAddNew2
    Dim avarFldNames As Variant
    Dim avarFldValues As Variant

    avarFldNames = Array("CompanyName", "Phone")
    avarFldValues = Array("Sample Shipper 2", "(931) 555-6334")

    If objRs1.Supports(adAddNew) Then
        objRs1.AddNew avarFldNames, avarFldValues
    End If

    'Re-establish a Connection and update
    Set objRs1.ActiveConnection = GetNewConnection
    objRs1.UpdateBatch
'EndAddNew2
```
