---
description: Ordinal, propriété (objet Cell d’ADO MD)
title: Propriété ordinale (cellule ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell::Ordinal
- Ordinal
helpviewer_keywords:
- Ordinal property [ADO MD]
ms.assetid: a6001168-b954-47f0-ba0d-c05c4cc40c58
author: rothja
ms.author: jroth
ms.openlocfilehash: a0217267b73a449e40beff1134b3cdcc744246f3
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777928"
---
# <a name="ordinal-property-ado-md-cell"></a>Ordinal, propriété (objet Cell d’ADO MD)
Identifie de façon unique une [cellule](./cell-object-ado-md.md) en fonction de sa position dans un CellSet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un entier **long** et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 La valeur ordinale de la cellule identifie de façon unique la cellule dans un CellSet. Conceptuellement, les cellules sont numérotées dans un ensemble de cellules comme si l’ensemble de cellules était un tableau de dimensions *p*, où *p* est le nombre d' [axes](./axes-collection-ado-md.md). Les cellules sont numérotées à partir de zéro dans l’ordre ligne-principal. Voici la formule permettant de calculer le nombre ordinal d’une cellule :  
  
 La valeur ordinale de la cellule peut être utilisée avec la propriété [Item](./item-property-ado-md-cellset.md) de l’objet [Cellset](./cellset-object-ado-md.md) pour récupérer rapidement la [cellule](./cell-object-ado-md.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Cell, objet (ADO MD)](./cell-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AXIS, exemple (VBScript)](./axis-example-vbscript.md)   
 [CellSet, objet (ADO MD)](./cellset-object-ado-md.md)   
 [Item, propriété (ADO MD CellSet)](./item-property-ado-md-cellset.md)   
 [Ordinal, propriété (objet Position d’ADO MD)](./ordinal-property-ado-md-position.md)