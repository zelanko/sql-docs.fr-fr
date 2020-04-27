---
title: Source, propriété (erreur ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::get_Source
- Error::Source
- Error::GetSource
helpviewer_keywords:
- Source property [ADO Error]
ms.assetid: 4044ba15-f013-4c4c-9fe1-b4410fe9a778
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6b55ebbe5a167b7d70cf606fc4e37e7ede36b486
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67916904"
---
# <a name="source-property-ado-error"></a>Source, propriété (objet Error ADO)
Indique le nom de l’objet ou de l’application qui a généré à l’origine une erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **chaîne** qui indique le nom d’un objet ou d’une application.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **source** sur un objet d' [erreur](../../../ado/reference/ado-api/error-object.md) pour déterminer le nom de l’objet ou de l’application qui a généré une erreur à l’origine. Il peut s’agir du nom de classe ou de l’ID programmatique de l’objet. Pour les erreurs dans ADO, la valeur de propriété sera **ADODB.** _ObjectName_, où *ObjectName* est le nom de l’objet qui a déclenché l’erreur. Pour ADOX et ADO MD, la valeur est **ADOX.** _ObjectName_ et **ADOMD.** _ObjectName_, respectivement.  
  
 En fonction de la documentation d’erreur des propriétés **source**, [Number](../../../ado/reference/ado-api/number-property-ado.md)et [Description](../../../ado/reference/ado-api/description-property.md) des objets **Error** , vous pouvez écrire du code qui traitera l’erreur de façon appropriée.  
  
 La propriété **source** est en lecture seule pour les objets d' **erreur** .  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Number, source et SQLState, exemples de propriétés (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Description, propriété](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext, HelpFile, propriétés](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number, propriété (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source, propriété (ADO record)](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Source, propriété (objet Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
