---
title: CellSet, objet (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset
helpviewer_keywords:
- Cellset object [ADO MD]
ms.assetid: 5e2452c0-cac0-49b2-8099-836c35794d50
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9524e9801f284d3dff3125b850cdd1fd32a361a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928645"
---
# <a name="cellset-object-ado-md"></a>Cellset, objet (ADO MD)
Représente les résultats d’une requête multidimensionnelle. Il s’agit d’une collection de cellules sélectionnées à partir de cubes ou d’autres cellules.  
  
## <a name="remarks"></a>Notes  
 Les données d’un ensemble de **cellules** sont récupérées à l’aide d’un accès direct de type tableau. Vous pouvez accéder à un membre spécifique pour obtenir des informations sur ce membre. Par exemple, le code suivant retourne la légende du premier membre de la première position sur le premier axe d’un CellSet nommé `cst`:  
  
```  
cst.Axes(0).Positions(0).Members(0).Caption  
```  
  
## <a name="remarks"></a>Notes  
 Il n’existe aucune notion de cellule active dans un CellSet. Au lieu de cela, la propriété [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) récupère un objet [Cell](../../../ado/reference/ado-md-api/cell-object-ado-md.md) spécifique du CellSet. Les arguments de la propriété de l' **élément** déterminent la cellule qui est récupérée. Vous pouvez spécifier la valeur ordinale unique d’une cellule. Vous pouvez également récupérer des cellules en utilisant leurs numéros de position le long de chaque axe de l’CellSet. Pour plus d’informations sur la récupération des cellules, consultez la propriété [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) .  
  
 Avec les collections, les méthodes et les propriétés d’un objet **Cellset** , vous pouvez effectuer les opérations suivantes :  
  
-   Associez une connexion ouverte à un objet **Cellset** en définissant sa propriété [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) .  
  
-   Exécutez et récupérez les résultats d’une requête multidimensionnelle à l’aide de la méthode [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md) .  
  
-   Récupérez une **cellule** de l' **Cellset** avec la propriété [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) .  
  
-   Retourne les objets [Axis](../../../ado/reference/ado-md-api/axis-object-ado-md.md) qui définissent l’ensemble de **cellules** avec la collection [axes](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) .  
  
-   Récupérez des informations sur les dimensions utilisées pour filtrer les données dans l' **Cellset** avec la propriété [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) .  
  
-   Retourne ou spécifie la requête utilisée pour définir l' **Cellset** avec la propriété [source](../../../ado/reference/ado-md-api/source-property-ado-md.md) .  
  
-   Retourne l’état actuel de l’objet **Cellset** (ouvert, fermé, en cours d’exécution ou en cours de connexion) avec la propriété [State](../../../ado/reference/ado-md-api/state-property-ado-md.md) .  
  
-   Fermez un **Cellset** ouvert avec la méthode [Close](../../../ado/reference/ado-md-api/close-method-ado-md.md) .  
  
-   Récupérez les informations spécifiques au fournisseur relatives à l’ensemble de **cellules** avec la collection de [Propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) ADO standard.  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/cellset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CellSet, exemple (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Axes, collection (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [Cell, objet (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
