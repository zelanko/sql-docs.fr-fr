---
description: Optimize, propriété dynamique (ADO)
title: Optimize, propriété dynamique (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Optimize property [ADO]
ms.assetid: a491c4ce-2b04-4c84-be83-3846bde8d16b
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ce2367d550cc8e420c4a1a9bf9fd10fff9e94e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442911"
---
# <a name="optimize-property-dynamic-ado"></a>Optimize, propriété dynamique (ADO)
Spécifie si un index doit être créé sur un [champ](../../../ado/reference/ado-api/field-object.md).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur **booléenne** qui indique si un index doit être créé.  
  
## <a name="remarks"></a>Notes  
 Un index peut améliorer les performances des opérations qui recherchent ou trient des valeurs dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). L’index est interne à ADO ; vous ne pouvez pas y accéder explicitement ou l’utiliser dans votre application.  
  
 Pour créer un index sur un champ, affectez la valeur **true**à la propriété **optimize** . Pour supprimer l’index, affectez la valeur **false**à cette propriété.  
  
 **Optimize** est une propriété dynamique ajoutée à la collection de [Propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) de l’objet [Field](../../../ado/reference/ado-api/field-object.md) lorsque la propriété [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) a la valeur **adUseClient**.  
  
## <a name="usage"></a>Usage  
  
```  
Dim rs As New Recordset  
Dim fld As Field  
rs.CursorLocation = adUseClient      'Enable index creation  
rs.Fields.Append "Field1", adChar, 35, adFldIsNullable  
rs.Open  
Set fld = rs.Fields(0)  
fld.Properties("Optimize") = True    'Create an index  
fld.Properties("Optimize") = False   'Delete an index  
```  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Optimize, exemple de propriété (VB)](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [Optimize, exemple de propriété (VC + +)](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [Filter (propriété)](../../../ado/reference/ado-api/filter-property.md)   
 [Find, méthode (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Sort, propriété](../../../ado/reference/ado-api/sort-property.md)
