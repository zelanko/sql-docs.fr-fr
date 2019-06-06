---
title: Objet de propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Property
helpviewer_keywords:
- Property object [ADO]
ms.assetid: b2a4767c-03c7-4935-a3bc-df3e1a38a009
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: af077c1606148eacb4f93ba6cfb52c3bb5eeefce
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702942"
---
# <a name="property-object-ado"></a>Property, objet (ADO)
Représente une caractéristique dynamique d’un objet ADO qui est définie par le fournisseur.  
  
## <a name="remarks"></a>Notes  
 Objets ADO possèdent deux types de propriétés : intégrées et dynamiques.  
  
 Propriétés intégrées sont les propriétés implémentées dans ADO et immédiatement disponibles pour tout nouvel objet, à l’aide du `MyObject.Property` syntaxe. Ils n’apparaissent pas en tant que **propriété** les objets d’un objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection, donc vous pouvez modifier leurs valeurs, vous ne pouvez pas modifier leurs caractéristiques.  
  
 Propriétés dynamiques sont définies par le fournisseur de données sous-jacent et apparaissent dans le **propriétés** collection pour l’objet ADO approprié. Par exemple, une propriété spécifique au fournisseur peut indiquer si un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet prend en charge les transactions ou la mise à jour. Ces propriétés supplémentaires apparaissent en tant que **propriété** objets dans ce **Recordset** l’objet **propriétés** collection. Propriétés dynamiques peuvent être référencées uniquement par le biais de la collection, à l’aide de la `MyObject.Properties(0)` ou `MyObject.Properties("Name")` syntaxe.  
  
 Vous ne pouvez pas supprimer un de ces types de propriété.  
  
 Dynamique **propriété** objet possède quatre propriétés intégrées :  
  
-   Le [nom](../../../ado/reference/ado-api/name-property-ado.md) propriété est une chaîne qui identifie la propriété.  
  
-   Le [Type](../../../ado/reference/ado-api/type-property-ado.md) propriété est un entier qui spécifie le type de données de propriété.  
  
-   Le [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété est une variante qui contient le paramètre de propriété. **Valeur** est la propriété par défaut pour un **propriété** objet.  
  
-   Le [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) propriété est une valeur longue qui indique les caractéristiques de la propriété spécifique au fournisseur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Objet de propriétés, méthodes et événements](../../../ado/reference/ado-api/property-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Objet Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Objet de champ](../../../ado/reference/ado-api/field-object.md)   
 [Collection de propriétés (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
