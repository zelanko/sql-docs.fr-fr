---
title: Ajout d’enregistrements | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- editing data [ADO], AddNew method
- editing data [ADO], adding data
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 87d8358344d75cd6995d43d081abbec7aeaabe1c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701058"
---
# <a name="adding-records-to-a-recordset"></a>Ajout d’enregistrements à un jeu d’enregistrements
Utilisez le **AddNew** méthode pour créer et initialiser un nouvel enregistrement dans une existante **Recordset**. Vous pouvez utiliser la **prend en charge** méthode avec un **CursorOptionEnum** valeur **adAddNew** pour vérifier si vous pouvez ajouter des enregistrements à actuel **Recordset** objet.

 Après avoir appelé la **AddNew** (méthode), le nouvel enregistrement devient l’enregistrement actif et reste actif après avoir appelé la **mise à jour** (méthode). Si le **Recordset** objet ne prend pas en charge les signets, vous n’êtes peut-être pas en mesure d’accéder au nouvel enregistrement lorsque vous passez à un autre enregistrement. Par conséquent, en fonction de votre type de curseur, vous devrez peut-être appeler le **Requery** méthode pour rendre le nouvel enregistrement accessible.

 Si vous appelez **AddNew** lors de la modification de l’enregistrement en cours ou lors de l’ajout d’un nouvel enregistrement, ADO appelle le **mise à jour** méthode pour enregistrer un change et puis crée le nouvel enregistrement.

 Cette section contient les rubriques suivantes.

-   [Ajout d’enregistrements avec AddNew](../../../ado/guide/data/adding-records-using-addnew.md)

-   [Ajout de plusieurs champs](../../../ado/guide/data/adding-multiple-fields.md)

-   [Détermination du mode d’édition](../../../ado/guide/data/determining-edit-mode.md)

-   [Utilisation d’AddNew dans les modes immédiat et batch](../../../ado/guide/data/using-addnew-in-immediate-and-batch-modes.md)
