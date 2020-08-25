---
description: State, propriété (ADO MD)
title: State, propriété (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- State
- Cellset::State
helpviewer_keywords:
- State property [ADO MD]
ms.assetid: 06d480ca-9eb6-4570-a45d-a73539bddd32
author: rothja
ms.author: jroth
ms.openlocfilehash: efc3b140b2864aec7151e1235010c4a14b0b3a64
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777858"
---
# <a name="state-property-ado-md"></a>State, propriété (ADO MD)
Indique l’état actuel du CellSet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un entier **long** indiquant la condition actuelle de l’objet [Cellset](./cellset-object-ado-md.md) et est en lecture seule. Les valeurs suivantes sont valides : **adStateClosed** (0) et **adStateOpen** (1).  
  
## <a name="remarks"></a>Notes  
 Pour utiliser les noms de constantes [ObjectStateEnum](../ado-api/objectstateenum.md) , vous devez disposer de la bibliothèque de types ADO référencée dans votre projet. Pour plus d’informations, consultez [utilisation d’ADO avec ADO MD](../../guide/multidimensional/using-ado-with-ado-md.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Cellset, objet (ADO MD)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Close, méthode (ADO MD)](./close-method-ado-md.md)   
 [Open, méthode (ADO MD)](./open-method-ado-md.md)