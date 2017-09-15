---
title: "DELETE, méthode (Collection de champs ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Fields20::Delete
- Fields20::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 25bedc25-c51c-4cab-96ce-930b959965d9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: de4e5f85bad4849f4ace2ee4e32fbe6606cb667d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="delete-method-ado-fields-collection"></a>DELETE, méthode (Collection de champs ADO)
Supprime un objet à partir de la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Field*  
 A **Variant** qui désigne le [champ](../../../ado/reference/ado-api/field-object.md) objet à supprimer. Ce paramètre peut être le nom de la **champ** objet ou la position ordinale de la **champ** objet lui-même.  
  
## <a name="remarks"></a>Notes  
 Appel de la **Fields.Delete** méthode sur open [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) provoque une erreur d’exécution.  
  
## <a name="applies-to"></a>S'applique à  
 [Collection de champs (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE, méthode (Collection de paramètres ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [DELETE, méthode (jeu d’enregistrements ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord, méthode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
