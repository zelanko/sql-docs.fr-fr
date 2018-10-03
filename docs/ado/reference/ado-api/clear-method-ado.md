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
manager: craigg
ms.openlocfilehash: 0e69e7d2d2a66ccb9df0e03f6f77849c502f3bf2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753217"
---
# <a name="clear-method-ado"></a>Clear, méthode (ADO)
Supprime tous les le [erreur](../../../ado/reference/ado-api/error-object.md) objets à partir de la [erreurs](../../../ado/reference/ado-api/errors-collection-ado.md) collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>Notes  
 Utilisez le **clair** méthode sur le [erreurs](../../../ado/reference/ado-api/errors-collection-ado.md) collection à supprimer toutes les existantes [erreur](../../../ado/reference/ado-api/error-object.md) objets à partir de la collection. Lorsqu’une erreur se produit, ADO efface automatiquement le **erreurs** collection et le remplit avec **erreur** objets basés sur la nouvelle erreur.  
  
 Certaines propriétés et méthodes retournent des avertissements qui apparaissent sous la forme **erreur** des objets dans le **erreurs** collection sans pour autant arrêter l’exécution d’un programme. Avant d’appeler le [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), ou [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) méthodes sur un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet ; la [ouvrir](../../../ado/reference/ado-api/open-method-ado-connection.md) méthode sur un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet ; ou définissez le [filtre](../../../ado/reference/ado-api/filter-property.md) propriété sur un **Recordset** d’objet, appelez le **effacer**(méthode) sur le **erreurs** collection. De cette façon, vous pouvez lire le [nombre](../../../ado/reference/ado-api/count-property-ado.md) propriété de la **erreurs** collection pour tester les avertissements retournés.  
  
## <a name="applies-to"></a>S'applique à  
 [Errors, collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Execute, Requery et Clear, exemple de méthodes (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery et Clear, exemple de méthodes (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery et Clear, exemple de méthodes (VC ++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CancelBatch, méthode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [DELETE, méthode (Collection de champs ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [DELETE, méthode (Collection de paramètres ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [DELETE, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Propriété de filtre](../../../ado/reference/ado-api/filter-property.md)   
 [Resync, méthode](../../../ado/reference/ado-api/resync-method.md)   
 [UpdateBatch, méthode](../../../ado/reference/ado-api/updatebatch-method.md)
