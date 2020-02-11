---
title: Clear, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Errors::raw_Clear
- Errors::Clear
helpviewer_keywords:
- Clear method [ADO]
ms.assetid: 0a61ba7a-20b8-426a-91a0-9040e7c5a98a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 96bd13f130966b1830d07e49633842e4154b52b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920066"
---
# <a name="clear-method-ado"></a>Clear, méthode (ADO)
Supprime tous les objets [Error](../../../ado/reference/ado-api/error-object.md) de la collection [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>Notes  
 Utilisez la méthode **Clear** de la collection [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) pour supprimer tous les objets d' [erreur](../../../ado/reference/ado-api/error-object.md) existants de la collection. Lorsqu’une erreur se produit, ADO efface automatiquement la collection d' **Erreurs** et la remplit avec des objets d' **erreur** en fonction de la nouvelle erreur.  
  
 Certaines propriétés et méthodes retournent des avertissements qui s’affichent en tant qu’objets d' **erreur** dans la collection d' **Erreurs** , mais n’arrêtent pas l’exécution d’un programme. Avant d’appeler les méthodes [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)ou [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) sur un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ; la méthode [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) sur un objet [Connection](../../../ado/reference/ado-api/connection-object-ado.md) ; ou définissez la propriété [Filter](../../../ado/reference/ado-api/filter-property.md) sur un objet **Recordset** , appelez la méthode **Clear** sur la collection **Errors** . De cette façon, vous pouvez lire la propriété [Count](../../../ado/reference/ado-api/count-property-ado.md) de la collection **Errors** pour tester les avertissements retournés.  
  
## <a name="applies-to"></a>S'applique à  
 [Errors, collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Execute, Requery et Clear, exemples de méthodes (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery et Clear, exemple de méthode (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery et Clear, exemples de méthodes (VC + +)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Méthode CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Delete, méthode (collection Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete, méthode (collection Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Filter (propriété)](../../../ado/reference/ado-api/filter-property.md)   
 [Resync, méthode](../../../ado/reference/ado-api/resync-method.md)   
 [UpdateBatch, méthode](../../../ado/reference/ado-api/updatebatch-method.md)
