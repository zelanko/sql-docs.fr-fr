---
title: Objet de propriété (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2502dcdab170102f526aa1ea0fe67235e6bf3048
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815597"
---
# <a name="property-object-adox"></a>Property, objet (ADOX)
Représente une caractéristique d’un objet ADOX.  
  
## <a name="remarks"></a>Notes  
 Objets ADOX ont deux types de propriétés : intégrées et dynamiques.  
  
 Les propriétés intégrées sont ces propriétés immédiatement disponibles pour tout nouvel objet, à l’aide de la syntaxe MyObject.Property. Ils n’apparaissent pas en tant qu’objets de propriété dans un objet [collection de propriétés](../../../ado/reference/ado-api/properties-collection-ado.md), de sorte que vous pouvez modifier leurs valeurs, vous ne pouvez pas modifier leurs caractéristiques.  
  
 Propriétés dynamiques sont définies par le fournisseur de données sous-jacent et apparaissent dans la collection de propriétés pour l’objet ADOX approprié.  Propriétés dynamiques peuvent être référencées uniquement par le biais de la collection, à l’aide de la syntaxe MyObject.Properties(0) ou MyObject.Properties("Name").  
  
 Vous ne pouvez pas supprimer un de ces types de propriété.  
  
 Un objet de propriété dynamique a quatre propriétés intégrées :  
  
 Le [nom](../../../ado/reference/ado-api/name-property-ado.md) propriété est une chaîne qui identifie la propriété.  
  
 Le [Type](../../../ado/reference/ado-api/type-property-ado.md) propriété est un entier qui spécifie le type de données de propriété.  
  
 Le [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété est une variante qui contient le paramètre de propriété. Valeur est la propriété par défaut pour un objet de propriété.  
  
 Le [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) propriété est une valeur longue qui indique les caractéristiques de la propriété spécifique au fournisseur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet Property](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
