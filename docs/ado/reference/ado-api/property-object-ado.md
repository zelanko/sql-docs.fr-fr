---
title: "Objet de propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Property
helpviewer_keywords:
- Property object [ADO]
ms.assetid: b2a4767c-03c7-4935-a3bc-df3e1a38a009
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4a0c5a1217cb8143a0b275ea3d0c31e16b7d1cd1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="property-object-ado"></a>Objet de propriété (ADO)
Représente une caractéristique dynamique d’un objet ADO qui est défini par le fournisseur.  
  
## <a name="remarks"></a>Notes  
 Objets ADO possèdent deux types de propriétés : intégrées et dynamiques.  
  
 Propriétés intégrées sont les propriétés implémentées dans ADO et immédiatement disponibles pour tout nouvel objet, à l’aide du `MyObject.Property` syntaxe. Ils n’apparaissent pas en tant que **propriété** les objets d’un objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection, donc vous pouvez modifier leurs valeurs, vous ne pouvez pas modifier leurs caractéristiques.  
  
 Les propriétés dynamiques sont définies par le fournisseur de données sous-jacent et apparaissent dans le **propriétés** collection pour l’objet ADO approprié. Par exemple, une propriété spécifique au fournisseur peut indiquer si un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet prend en charge les transactions ou la mise à jour. Ces propriétés supplémentaires apparaissent en tant que **propriété** objets dans ce **Recordset** l’objet **propriétés** collection. Propriétés dynamiques peuvent être référencées uniquement par le biais de la collection, à l’aide de la `MyObject.Properties(0)` ou `MyObject.Properties("Name")` syntaxe.  
  
 Vous ne pouvez pas supprimer les deux types de propriété.  
  
 Un dynamique **propriété** objet possède quatre propriétés intégrées :  
  
-   Le [nom](../../../ado/reference/ado-api/name-property-ado.md) propriété est une chaîne qui identifie la propriété.  
  
-   Le [Type](../../../ado/reference/ado-api/type-property-ado.md) propriété est un entier qui spécifie le type de données de propriété.  
  
-   Le [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété est une variante qui contient le paramètre de propriété. **Valeur** est la propriété par défaut pour un **propriété** objet.  
  
-   Le [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) propriété est une valeur de type long qui indique les caractéristiques de la propriété spécifique au fournisseur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Objet de propriétés, méthodes et événements](../../../ado/reference/ado-api/property-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de commande (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Objet de connexion (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Objet Field](../../../ado/reference/ado-api/field-object.md)   
 [Collection de propriétés (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)

