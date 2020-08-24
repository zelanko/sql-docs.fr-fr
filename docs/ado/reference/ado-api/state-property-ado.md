---
description: State, propriété (ADO)
title: State, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command25::State
helpviewer_keywords:
- State property [ADO]
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
author: rothja
ms.author: jroth
ms.openlocfilehash: 14e9a083c9f80d2c6485a9444211a2796b7fabee
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777348"
---
# <a name="state-property-ado"></a>State, propriété (ADO)
Indique pour tous les objets applicables si l’état de l’objet est ouvert ou fermé. Si l’objet exécute une méthode asynchrone, indique si l’état actuel de l’objet est en cours de connexion, en cours d’exécution ou en cours d’extraction.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **type long** qui peut être une valeur [ObjectStateEnum](./objectstateenum.md) . La valeur par défaut est **adStateClosed**.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la propriété **State** pour déterminer l’état actuel d’un objet donné à tout moment.  
  
 La propriété **State** de l’objet peut avoir une combinaison de valeurs. Par exemple, si une instruction est en cours d’exécution, cette propriété aura une valeur combinée de **adStateOpen** et **adStateExecuting**.  
  
 La propriété d' **État** est en lecture seule.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Command, objet (ADO)](./command-object-ado.md)  
        [Connection, objet (ADO)](./connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Record, objet (ADO)](./record-object-ado.md)  
        [Recordset, objet (ADO)](./recordset-object-ado.md)  
    :::column-end:::
    :::column:::
        [Stream, objet (ADO)](./stream-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [ConnectionString, ConnectionTimeout et State, exemple de propriétés (VB)](./connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout et State, exemple de propriétés (VC + +)](./connectionstring-connectiontimeout-and-state-properties-example-vc.md)