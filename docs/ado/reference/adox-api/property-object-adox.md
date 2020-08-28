---
description: Property, objet (ADOX)
title: Property, objet (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b2cfa49dcab6c3bc3b56ab5f2d987c026fa3f85
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983460"
---
# <a name="property-object-adox"></a>Property, objet (ADOX)
Représente une caractéristique d’un objet ADOX.  
  
## <a name="remarks"></a>Notes  
 Les objets ADOX ont deux types de propriétés : intégré et dynamique.  
  
 Les propriétés intégrées sont les propriétés immédiatement disponibles pour tout nouvel objet, à l’aide de la syntaxe MyObject. Property. Ils n’apparaissent pas en tant qu’objets de propriété dans la [collection de propriétés](../ado-api/properties-collection-ado.md)d’un objet. par conséquent, bien que vous puissiez modifier leurs valeurs, vous ne pouvez pas modifier leurs caractéristiques.  
  
 Les propriétés dynamiques sont définies par le fournisseur de données sous-jacent et s’affichent dans la collection Properties pour l’objet ADOX approprié.  Les propriétés dynamiques peuvent être référencées uniquement par le biais de la collection, à l’aide de la syntaxe MyObject. Properties (0) ou MyObject. Properties ("Name").  
  
 Vous ne pouvez pas supprimer un type de propriété.  
  
 Un objet de propriété dynamique a quatre propriétés intégrées :  
  
 La propriété [Name](../ado-api/name-property-ado.md) est une chaîne qui identifie la propriété.  
  
 La propriété de [type](../ado-api/type-property-ado.md) est un entier qui spécifie le type de données de la propriété.  
  
 La propriété [valeur](../ado-api/value-property-ado.md) est un variant qui contient le paramètre de propriété. La valeur est la propriété par défaut d’un objet de propriété.  
  
 La propriété [attributes](../ado-api/attributes-property-ado.md) est une valeur de type long qui indique les caractéristiques de la propriété spécifique au fournisseur.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements de l’objet Property ADOX](./adox-property-object-properties-methods-and-events.md)