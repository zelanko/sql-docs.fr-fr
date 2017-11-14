---
title: "DELETE, méthode (Collection de paramètres ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _DynaCollection::Delete
- _DynaCollection::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 160c575e-df63-4ade-a2d3-5fd8f72e70cc
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 770271da0c0b2b378adf2be5611428e05f7f5148
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="delete-method-ado-parameters-collection"></a>DELETE, méthode (Collection de paramètres ADO)
Supprime un objet à partir de la [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Parameters.Delete Index  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Index*  
 A **chaîne** valeur qui contient le nom de l’objet à supprimer, ou la position ordinale de l’objet (index) dans la collection.  
  
## <a name="remarks"></a>Notes  
 À l’aide de la **supprimer** méthode sur une collection vous permet de supprimer un des objets dans la collection. Cette méthode est uniquement disponible sur le **paramètres** collection d’un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet. Vous devez utiliser le [paramètre](../../../ado/reference/ado-api/parameter-object.md) l’objet [nom](../../../ado/reference/ado-api/name-property-ado.md) propriété ou son index de collection lorsque vous appelez le **supprimer** (méthode), une variable objet n’est pas un argument valide.  
  
## <a name="applies-to"></a>S'applique à  
 [Collection de paramètres (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE, méthode (Collection de champs ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [DELETE, méthode (jeu d’enregistrements ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord, méthode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)

