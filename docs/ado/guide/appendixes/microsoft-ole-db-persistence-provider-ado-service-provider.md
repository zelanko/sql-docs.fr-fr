---
description: Fournisseur de persistance Microsoft OLE DB (fournisseur de services ADO)
title: Fournisseur de persistance Microsoft OLE DB (fournisseur de services ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB persistence provider
- persistence provider [ADO]
- OLE DB persistence provider [ADO]
ms.assetid: e75ef0dc-2016-4fcc-8918-23311c0d4e02
author: rothja
ms.author: jroth
ms.openlocfilehash: fe50ef2d018f01e0811c5d950f73ae6cb3d3c5f3
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97638058"
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Présentation du fournisseur de persistance Microsoft OLE DB
Le fournisseur de persistance Microsoft OLE DB vous permet d’enregistrer un objet [Recordset](../../reference/ado-api/recordset-object-ado.md) dans un fichier et de restaurer ultérieurement cet objet **Recordset** à partir du fichier. Les informations de schéma, les données et les modifications en attente sont conservées.

 Vous pouvez enregistrer le **Recordset** au format ADTG (Advanced Data table) propriétaire ou au format Open Extensible Markup Language (XML).

## <a name="provider-keyword"></a>Mot clé Provider
 Pour appeler ce fournisseur, spécifiez le mot clé et la valeur suivants dans la chaîne de connexion.

```vb
"Provider=MSPersist"
```

## <a name="errors"></a>Erreurs
 Les erreurs suivantes émises par ce fournisseur peuvent être détectées dans votre application.

|Constante|Description|
|--------------|-----------------|
|E_BADSTREAM|Le format du fichier ouvert n’est pas valide (autrement dit, le format n’est pas ADTG ou XML).|
|E_CANTPERSISTROWSET|L’objet **Recordset** enregistré possède des caractéristiques qui empêchent son stockage.|

## <a name="remarks"></a>Remarques
 Le fournisseur de persistance Microsoft OLE DB n’expose aucune propriété dynamique.

 Actuellement, seuls les objets **Recordset** hiérarchiques paramétrables ne peuvent pas être enregistrés.

 Pour plus d’informations sur le stockage permanent d’objets **Recordset** , consultez [persistance des recordsets](../data/more-about-recordset-persistence.md).

 Lorsqu’un flux est utilisé pour ouvrir un **jeu d’enregistrements,** aucun paramètre ne doit être spécifié autre que le paramètre *source* de la méthode **Open** .
