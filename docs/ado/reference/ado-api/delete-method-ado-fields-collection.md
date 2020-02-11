---
title: Delete, méthode (collection Fields ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields20::Delete
- Fields20::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 25bedc25-c51c-4cab-96ce-930b959965d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9db49905b6548e5cb21cca976683c8b387017d32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919131"
---
# <a name="delete-method-ado-fields-collection"></a>Delete, méthode (collection Fields ADO)
Supprime un objet de la collection de [champs](../../../ado/reference/ado-api/fields-collection-ado.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Champ*  
 **Variante** qui désigne l’objet de [champ](../../../ado/reference/ado-api/field-object.md) à supprimer. Ce paramètre peut être le nom de l’objet de **champ** ou la position ordinale de l’objet de **champ** lui-même.  
  
## <a name="remarks"></a>Notes  
 L’appel de la méthode **Fields. Delete** sur un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ouvert provoque une erreur au moment de l’exécution.  
  
## <a name="applies-to"></a>S'applique à  
 [Fields, collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Delete, méthode (collection Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord, méthode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
