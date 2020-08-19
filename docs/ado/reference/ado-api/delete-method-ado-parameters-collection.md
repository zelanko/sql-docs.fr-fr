---
description: Delete, méthode (collection Parameters ADO)
title: Delete, méthode (collection Parameters ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Delete
- _DynaCollection::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 160c575e-df63-4ade-a2d3-5fd8f72e70cc
author: rothja
ms.author: jroth
ms.openlocfilehash: a76353f62fc2b30ea8e7eae16c97469027a98110
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444161"
---
# <a name="delete-method-ado-parameters-collection"></a>Delete, méthode (collection Parameters ADO)
Supprime un objet de la collection de [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Parameters.Delete Index  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Index*  
 Valeur de **chaîne** qui contient le nom de l’objet à supprimer ou la position ordinale (index) de l’objet dans la collection.  
  
## <a name="remarks"></a>Notes  
 L’utilisation de la méthode **Delete** sur une collection vous permet de supprimer l’un des objets de la collection. Cette méthode est uniquement disponible dans la collection **Parameters** d’un objet [Command](../../../ado/reference/ado-api/command-object-ado.md) . Vous devez utiliser la propriété [Name](../../../ado/reference/ado-api/name-property-ado.md) de l’objet [Parameter](../../../ado/reference/ado-api/parameter-object.md) ou son index de collection lors de l’appel de la méthode **Delete** . une variable objet n’est pas un argument valide.  
  
## <a name="applies-to"></a>S'applique à  
 [Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Delete, méthode (collection Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord, méthode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
