---
title: Item, propriété (objet Cellset d’ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Item
- Cellset::Item
helpviewer_keywords:
- Item property [ADO MD]
ms.assetid: 0e93d79b-b12e-4e98-889e-c2dfcca20fd0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 68191a6d6e8541eb89a7c4be3c6820b2627fc90a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66709236"
---
# <a name="item-property-ado-md-cellset"></a>Item, propriété (objet Cellset d’ADO MD)
Récupère une cellule à partir d’un [cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) à l’aide de ses coordonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set  
Cell = Cellset.Item ( Positions)  
```  
  
## <a name="parameters"></a>Paramètres  
 *Positions*  
 Un **VariantArray** des valeurs qui spécifient de manière unique une cellule. *Positions* peut prendre l’une des opérations suivantes :  
  
-   Un tableau de nombres de position  
  
-   Un tableau de noms de membre  
  
-   La position ordinale  
  
## <a name="remarks"></a>Notes  
 Utilisez le **élément** propriété à retourner un [cellule](../../../ado/reference/ado-md-api/cell-object-ado-md.md) de l’objet dans un [ensemble de cellules](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objet. Si le **élément** propriété ne peut pas trouver la cellule correspondant à la *Positions* argument, une erreur se produit.  
  
 Le **élément** propriété est la propriété par défaut pour le **Cellset** objet. Les formes de syntaxe suivantes sont interchangeables :  
  
```  
  
Cellset.Item ( Positions )Cellset ( Positions )  
```  
  
## <a name="remarks"></a>Notes  
 Le *Positions* argument spécifie la cellule à retourner. Vous pouvez spécifier la cellule par position ordinale ou par la position le long de chaque axe. Lorsque vous spécifiez la cellule par position le long de chaque axe, vous pouvez spécifier la valeur numérique de la position ou les noms des membres pour chaque position.  
  
 La position ordinale est un nombre qui identifie de façon unique une cellule dans le **Cellset**. Conceptuellement, les cellules sont comptabilisées dans un **Cellset** comme si le **Cellset** ont été un *p*-tableau unidimensionnel, où *p* est le nombre d’axes. Les cellules sont traitées dans l'ordre ligne-champ. Voici la formule pour calculer le nombre ordinal d’une cellule :  
  
 Si des noms de membres sont passés comme des chaînes à **élément**, les membres doivent figurer dans l’ordre des identificateurs de l’axe numérique croissant. Au sein d’un axe, les membres doivent être répertoriés en ordre croissant d’imbrication : autrement dit, les membres de la dimension la plus éloignée vient en premier, suivie des dimensions. Chaque dimension doit être représentée par une chaîne séparée, et la liste de chaînes de membre doit être séparée par des virgules.  
  
> [!NOTE]
>  Extraction des cellules par nom de membre ne peut pas être pris en charge par votre fournisseur de données. Consultez la documentation de votre fournisseur pour plus d’informations.  
  
## <a name="applies-to"></a>S'applique à  
 [Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Cellule, objet (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)
