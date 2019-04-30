---
title: DELETE, méthode (Collection de champs ADO) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 097286f14de4dead4490c322615a6405c157f118
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140249"
---
# <a name="delete-method-ado-fields-collection"></a>Delete, méthode (collection Fields ADO)
Supprime un objet à partir de la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Field*  
 Un **Variant** qui désigne le [champ](../../../ado/reference/ado-api/field-object.md) objet à supprimer. Ce paramètre peut être le nom de la **champ** objet ou la position ordinale de la **champ** objet lui-même.  
  
## <a name="remarks"></a>Notes  
 Appel de la **Fields.Delete** méthode sur une ouverte [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) provoque une erreur d’exécution.  
  
## <a name="applies-to"></a>S'applique à  
 [Fields, collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE, méthode (Collection de paramètres ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [DELETE, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord, méthode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
