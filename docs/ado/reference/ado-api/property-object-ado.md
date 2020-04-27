---
title: Property, objet (ADO) | Microsoft Docs
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
ms.openlocfilehash: 43bfa816a9ca8a93cdc1188a98e54d3e0d9111b1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917552"
---
# <a name="property-object-ado"></a>Property, objet (ADO)
Représente une caractéristique dynamique d’un objet ADO qui est défini par le fournisseur.  
  
## <a name="remarks"></a>Notes  
 Les objets ADO ont deux types de propriétés : intégré et dynamique.  
  
 Les propriétés intégrées sont les propriétés implémentées dans ADO et immédiatement disponibles pour tout nouvel objet, à l' `MyObject.Property` aide de la syntaxe. Ils n’apparaissent pas en tant qu’objets de **propriété** dans la collection de [Propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) d’un objet. par conséquent, bien que vous puissiez modifier leurs valeurs, vous ne pouvez pas modifier leurs caractéristiques.  
  
 Les propriétés dynamiques sont définies par le fournisseur de données sous-jacent et s’affichent dans la collection **Properties** pour l’objet ADO approprié. Par exemple, une propriété spécifique au fournisseur peut indiquer si un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) prend en charge les transactions ou la mise à jour. Ces propriétés supplémentaires s’affichent sous la forme d’objets de **propriété** dans la collection de **Propriétés** de cet objet **Recordset** . Les propriétés dynamiques peuvent être référencées uniquement par l’intermédiaire de la `MyObject.Properties(0)` collection `MyObject.Properties("Name")` , à l’aide de la syntaxe ou.  
  
 Vous ne pouvez pas supprimer un type de propriété.  
  
 Un objet de **propriété** dynamique a quatre propriétés intégrées :  
  
-   La propriété [Name](../../../ado/reference/ado-api/name-property-ado.md) est une chaîne qui identifie la propriété.  
  
-   La propriété de [type](../../../ado/reference/ado-api/type-property-ado.md) est un entier qui spécifie le type de données de la propriété.  
  
-   La propriété [valeur](../../../ado/reference/ado-api/value-property-ado.md) est un variant qui contient le paramètre de propriété. La **valeur** est la propriété par défaut d’un objet de **propriété** .  
  
-   La propriété [attributes](../../../ado/reference/ado-api/attributes-property-ado.md) est une valeur de type long qui indique les caractéristiques de la propriété spécifique au fournisseur.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Property](../../../ado/reference/ado-api/property-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Field, objet](../../../ado/reference/ado-api/field-object.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
