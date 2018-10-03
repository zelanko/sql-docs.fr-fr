---
title: DELETE, méthode (Collection de paramètres ADO) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8eb7d5d58e0f6afe31304b6fce13da2d8c48e54e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696918"
---
# <a name="delete-method-ado-parameters-collection"></a>Delete, méthode (collection Parameters ADO)
Supprime un objet à partir de la [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Parameters.Delete Index  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Index*  
 Un **chaîne** valeur qui contient le nom de l’objet que vous souhaitez supprimer, ou position ordinale de l’objet (index) dans la collection.  
  
## <a name="remarks"></a>Notes  
 À l’aide de la **supprimer** méthode sur une collection vous permet de supprimer un des objets dans la collection. Cette méthode est uniquement disponible sur le **paramètres** collection d’un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet. Vous devez utiliser le [paramètre](../../../ado/reference/ado-api/parameter-object.md) l’objet [nom](../../../ado/reference/ado-api/name-property-ado.md) propriété ou son index de collection lorsque vous appelez le **supprimer** (méthode), une variable objet n’est pas un argument valide.  
  
## <a name="applies-to"></a>S'applique à  
 [Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE, méthode (Collection de champs ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [DELETE, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord, méthode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
