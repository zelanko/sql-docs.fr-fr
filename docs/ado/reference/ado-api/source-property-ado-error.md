---
title: Source, propriété (objet Error ADO) | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916904"
---
# <a name="source-property-ado-error"></a>Source, propriété (objet Error ADO)
Indique le nom de l’objet ou l’application qui a généré une erreur.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **chaîne** valeur qui indique le nom d’un objet ou l’application.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **Source** propriété sur une [erreur](../../../ado/reference/ado-api/error-object.md) objet pour déterminer le nom de l’objet ou l’application qui a généré une erreur. Il peut s’agir de l’objet nom de la classe ou l’ID programmatique. Pour les erreurs dans ADO, la valeur de propriété sera **ADODB.** _ObjectName_, où *ObjectName* est le nom de l’objet qui a déclenché l’erreur. Pour ADOX et ADO MD, la valeur sera **ADOX.** _ObjectName_ et **ADOMD.** _ObjectName_, respectivement.  
  
 Selon la documentation de l’erreur à partir de la **Source**, [nombre](../../../ado/reference/ado-api/number-property-ado.md), et [Description](../../../ado/reference/ado-api/description-property.md) propriétés de **erreur** objets, vous pouvez écrire du code qui gère l’erreur en conséquence.  
  
 Le **Source** propriété est en lecture seule pour **erreur** objets.  
  
## <a name="applies-to"></a>S'applique à  
 [Error, objet](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, nombre, Source et SQLState, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Propriété Description](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext, HelpFile, propriétés](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Number, propriété (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Source, propriété (objet Record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Source, propriété (objet Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
