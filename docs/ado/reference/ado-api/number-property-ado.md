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
manager: craigg
ms.openlocfilehash: afc9955920784af966ef5d793d76ce251df1bc1d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242665"
---
# <a name="number-property-ado"></a>Number, propriété (ADO)
Indique le numéro qui identifie de façon unique un [erreur](../../../ado/reference/ado-api/error-object.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Long** valeur pouvant correspondre à un de le [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) constantes.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **nombre** propriété afin de déterminer quelle erreur s’est produite. La valeur de la propriété est un nombre unique qui correspond à la condition d’erreur.  
  
 Le [erreurs](../../../ado/reference/ado-api/errors-collection-ado.md) collection retourne un HRESULT dans un format hexadécimal (par exemple, 0 x 80004005) ou une valeur longue (par exemple, 2147467259). Ces HRESULT peuvent être déclenchés par des composants sous-jacents, tels que OLE DB ou même OLE. Pour plus d’informations sur ces numéros, consultez [erreurs (OLE DB)](https://msdn.microsoft.com/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd) dans le [de référence du programmeur OLE DB](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)*.*  
  
## <a name="applies-to"></a>S'applique à  
 [Error, objet](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Propriété Description](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext, HelpFile, propriétés](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Source, propriété (objet Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
