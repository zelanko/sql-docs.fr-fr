---
title: Number, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce027747c843e02998f4845db7075e70cf8733b6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917997"
---
# <a name="number-property-ado"></a>Number, propriété (ADO)
Indique le nombre qui identifie de façon unique un objet d' [erreur](../../../ado/reference/ado-api/error-object.md) .  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **type long** qui peut correspondre à l’une des constantes [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) .  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **Number** pour déterminer l’erreur qui s’est produite. La valeur de la propriété est un nombre unique qui correspond à la condition d’erreur.  
  
 La collection [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) renvoie un HRESULT au format hexadécimal (par exemple, 0x80004005) ou une valeur long (par exemple, 2147467259). Ces HRESULT peuvent être déclenchés par des composants sous-jacents, tels que OLE DB ou même OLE lui-même. Pour plus d’informations sur ces nombres, consultez [Erreurs (OLE DB)](https://msdn.microsoft.com/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd) dans le [Guide de référence du programmeur OLE DB](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)*.*  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description, propriété](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext, HelpFile, propriétés](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Source, propriété (objet Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
