---
description: Optimize, propriété dynamique (ADO)
title: Optimize, propriété dynamique (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 3393bbfbfbaeb50c6a608db92dae42bb29fb3b1d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990260"
---
# <a name="optimize-property-dynamic-ado"></a>Optimize, propriété dynamique (ADO)
Spécifie si un index doit être créé sur un [champ](./field-object.md).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur **booléenne** qui indique si un index doit être créé.  
  
## <a name="remarks"></a>Notes  
 Un index peut améliorer les performances des opérations qui recherchent ou trient des valeurs dans un [Recordset](./recordset-object-ado.md). L’index est interne à ADO ; vous ne pouvez pas y accéder explicitement ou l’utiliser dans votre application.  
  
 Pour créer un index sur un champ, affectez la valeur **true**à la propriété **optimize** . Pour supprimer l’index, affectez la valeur **false**à cette propriété.  
  
 **Optimize** est une propriété dynamique ajoutée à la collection de [Propriétés](./properties-collection-ado.md) de l’objet [Field](./field-object.md) lorsque la propriété [CursorLocation](./cursorlocation-property-ado.md) a la valeur **adUseClient**.  
  
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
 [Objet Field](./field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Optimize, exemple de propriété (VB)](./optimize-property-example-vb.md)   
 [Optimize, exemple de propriété (VC + +)](./optimize-property-example-vc.md)   
 [Filter (propriété)](./filter-property.md)   
 [Find, méthode (ADO)](./find-method-ado.md)   
 [Sort, propriété](./sort-property.md)