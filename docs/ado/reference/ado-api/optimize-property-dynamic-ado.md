---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0b73e699141e598115f9ce178b74d10cbf22b0f5
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719156"
---
# <a name="optimize-property-dynamic-ado"></a>Optimize, propriété dynamique (ADO)
Spécifie si un index doit être créé sur un [champ](../../../ado/reference/ado-api/field-object.md).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **booléenne** valeur qui indique si un index doit être créé.  
  
## <a name="remarks"></a>Notes  
 Un index peut améliorer les performances des opérations de rechercher ou trier les valeurs dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). L’index est interne à ADO ; Vous ne peut pas explicitement accéder ou l’utiliser dans votre application.  
  
 Pour créer un index sur un champ, définissez la **optimiser** propriété **True**. Pour supprimer l’index, définissez cette propriété sur **False**.  
  
 **Optimiser** est une propriété dynamique ajoutée à la [champ](../../../ado/reference/ado-api/field-object.md) objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection lorsque le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété est définie sur **adUseClient**.  
  
## <a name="usage"></a>Utilisation  
  
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
 [Field, objet](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Optimize, exemple de propriété (VB)](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [Optimize, exemple de propriété (VC ++)](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [Propriété de filtre](../../../ado/reference/ado-api/filter-property.md)   
 [Rechercher, méthode (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Sort, propriété](../../../ado/reference/ado-api/sort-property.md)
