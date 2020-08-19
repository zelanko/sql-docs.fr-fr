---
description: Cell, objet (ADO MD)
title: Cell, objet (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell
helpviewer_keywords:
- Cell object [ADO MD]
ms.assetid: dcc2f044-b785-4a29-9bc5-b673f66eedf9
author: rothja
ms.author: jroth
ms.openlocfilehash: a6cb4d32a4a527cce7bc69eb39f8829bbf5cf58a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441241"
---
# <a name="cell-object-ado-md"></a>Cell, objet (ADO MD)
Représente les données à l’intersection des coordonnées d’axe contenues dans un CellSet.  
  
## <a name="remarks"></a>Notes  
 Un objet **Cell** est retourné par la propriété [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) d’un objet [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) .  
  
 Avec les collections et les propriétés d’un objet **Cell** , vous pouvez effectuer les opérations suivantes :  
  
-   Retourne les données de la **cellule** avec la propriété [value](../../../ado/reference/ado-md-api/value-property-ado-md.md) .  
  
-   Retourne la chaîne représentant l’affichage mis en forme de la propriété **value** avec la propriété [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md) .  
  
-   Retourne la valeur ordinale de la **cellule** dans l' **Cellset** avec la propriété [ordinal](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md) .  
  
-   Détermine la position de la **cellule** dans l' [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) avec la collection de [positions](../../../ado/reference/ado-md-api/positions-collection-ado-md.md) .  
  
-   Récupérez d’autres informations sur la **cellule** à l’aide de la collection de [Propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) ADO standard.  
  
 La collection **Properties** contient des propriétés fournies par le fournisseur. Le tableau suivant répertorie les propriétés qui peuvent être disponibles. La liste de propriétés réelle peut varier en fonction de l’implémentation du fournisseur. Pour obtenir une liste plus complète des propriétés disponibles, consultez la documentation de votre fournisseur.  
  
|Nom|Description|  
|----------|-----------------|  
|CouleurFond|Couleur d’arrière-plan utilisée lors de l’affichage de la cellule.|  
|FontFlags|Masque de masque détaillant les effets sur la police.|  
|FontName|Police utilisée pour afficher la valeur de la cellule.|  
|FontSize|Taille de police utilisée pour afficher la valeur de la cellule.|  
|CouleurTexte|Couleur de premier plan utilisée lors de l’affichage de la cellule.|  
|FormatString|Valeur dans une chaîne mise en forme.|  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AXIS, exemple (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [CellSet, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Collection positions (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
