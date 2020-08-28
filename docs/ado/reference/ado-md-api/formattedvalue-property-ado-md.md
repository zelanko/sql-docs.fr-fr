---
description: FormattedValue, propriété (ADO MD)
title: FormattedValue, propriété (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell::FormattedValue
- FormattedValue
helpviewer_keywords:
- FormattedValue property [ADO MD]
ms.assetid: 5c06451e-06ec-4da6-9a87-2d043469248a
author: rothja
ms.author: jroth
ms.openlocfilehash: 5905b4aba040505c60fa78721718b3ab03c51622
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986700"
---
# <a name="formattedvalue-property-ado-md"></a>FormattedValue, propriété (ADO MD)
Indique l’affichage mis en forme d’une valeur de [cellule](./cell-object-ado-md.md) .  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne une **chaîne** et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **FormattedValue** pour obtenir la valeur d’affichage mise en forme de la propriété [value](./value-property-ado-md.md) d’un objet [Cell](./cell-object-ado-md.md) . Par exemple, si la valeur d’une cellule était 1056,87 et que cette valeur représente un montant en dollars, **FormattedValue** serait $1 056,87.  
  
## <a name="applies-to"></a>S'applique à  
 [Cell, objet (ADO MD)](./cell-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CellSet, exemple (VB)](./cellset-example-vb.md)   
 [Value, propriété (ADO MD)](./value-property-ado-md.md)