---
title: "Objet de propriété (ADOX) | Documents Microsoft"
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
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fa319e0fa981b3346232e3d3848bfdfe843d9f31
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="property-object-adox"></a>Objet de propriété (ADOX)
Représente une caractéristique d’un objet ADOX.  
  
## <a name="remarks"></a>Notes  
 Les objets ADOX ont deux types de propriétés : intégrées et dynamiques.  
  
 Les propriétés intégrées sont les propriétés immédiatement disponibles pour tout nouvel objet, à l’aide de la syntaxe MyObject.Property. Ils n’apparaissent pas en tant qu’objets de propriété dans un objet [collection de propriétés](../../../ado/reference/ado-api/properties-collection-ado.md), de sorte que vous pouvez modifier leurs valeurs, vous ne pouvez pas modifier leurs caractéristiques.  
  
 Propriétés dynamiques sont définies par le fournisseur de données sous-jacent et apparaissent dans la collection de propriétés de l’objet ADOX approprié.  Propriétés dynamiques peuvent être référencées uniquement par le biais de la collection, à l’aide de la syntaxe MyObject.Properties(0) ou MyObject.Properties("Name").  
  
 Vous ne pouvez pas supprimer les deux types de propriété.  
  
 Un objet de propriété dynamique possède quatre propriétés intégrées :  
  
 Le [nom](../../../ado/reference/ado-api/name-property-ado.md) propriété est une chaîne qui identifie la propriété.  
  
 Le [Type](../../../ado/reference/ado-api/type-property-ado.md) propriété est un entier qui spécifie le type de données de propriété.  
  
 Le [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété est une variante qui contient le paramètre de propriété. Valeur est la propriété par défaut pour un objet de propriété.  
  
 Le [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) propriété est une valeur de type long qui indique les caractéristiques de la propriété spécifique au fournisseur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés de l’objet ADOX propriétés, méthodes et événements](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)

