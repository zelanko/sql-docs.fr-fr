---
title: Item, propriété (ADO MD CellSet) | Microsoft Docs
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
ms.openlocfilehash: 0c7fbce544cac188db7ed3b3d40478aa63809405
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949626"
---
# <a name="item-property-ado-md-cellset"></a>Item, propriété (objet Cellset d’ADO MD)
Récupère une cellule d’un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) à l’aide de ses coordonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set  
Cell = Cellset.Item ( Positions)  
```  
  
## <a name="parameters"></a>Paramètres  
 *Positions*  
 **VariantArray** de valeurs qui spécifient une cellule de façon unique. Les *positions* peuvent être l’une des suivantes :  
  
-   Tableau de numéros de position  
  
-   Tableau de noms de membres  
  
-   Position ordinale  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **Item** pour retourner un objet [Cell](../../../ado/reference/ado-md-api/cell-object-ado-md.md) dans un objet [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) . Si la propriété **Item** ne peut pas trouver la cellule correspondant à l’argument *positions* , une erreur se produit.  
  
 La propriété **Item** est la propriété par défaut de l’objet **Cellset** . Les formes de syntaxe suivantes sont interchangeables :  
  
```  
  
Cellset.Item ( Positions )Cellset ( Positions )  
```  
  
## <a name="remarks"></a>Notes  
 L’argument *positions* spécifie la cellule à retourner. Vous pouvez spécifier la cellule en fonction de la position ordinale ou de la position le long de chaque axe. Lorsque vous spécifiez la cellule par position le long de chaque axe, vous pouvez spécifier la valeur numérique de la position ou les noms des membres de chaque position.  
  
 La position ordinale est un nombre qui identifie de façon unique une cellule dans l' **Cellset**. Conceptuellement, les cellules sont numérotées dans un ensemble de **cellules** comme si l’ensemble de **cellules** était un tableau de dimensions *p*, où *p* est le nombre d’axes. Les cellules sont traitées dans l'ordre ligne-champ. Vous trouverez ci-dessous la formule permettant de calculer le nombre ordinal d’une cellule :  
  
 Si les noms de membres sont passés en tant que chaînes à **Item**, les membres doivent être répertoriés dans l’ordre de tri des identificateurs d’axe numérique. Dans un axe, les membres doivent être listés dans l’ordre de plus en plus important de l’imbrication de dimensions, autrement dit, le membre de la dimension la plus à l’extérieur est d’abord suivi des membres de dimensions internes. Chaque dimension doit être représentée par une chaîne distincte, et la liste des chaînes de membres doit être séparée par des virgules.  
  
> [!NOTE]
>  La récupération de cellules par nom de membre peut ne pas être prise en charge par votre fournisseur de données. Pour plus d’informations, consultez la documentation de votre fournisseur.  
  
## <a name="applies-to"></a>S'applique à  
 [Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Cell, objet (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)
