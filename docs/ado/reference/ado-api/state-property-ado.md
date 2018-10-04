---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98d3e61b37eb22ebaf793252f49b2b11621abd80
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47659357"
---
# <a name="state-property-ado"></a>State, propriété (ADO)
Indique, pour tous les objets applicables si l’état de l’objet est ouvert ou fermé. Si l’objet s’exécute une méthode asynchrone, indique l’état actuel de l’objet se connecte, l’exécution ou récupération.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Long** valeur qui peut être un [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) valeur. La valeur par défaut est **adStateClosed**.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la **état** propriété afin de déterminer l’état actuel d’un objet donné à tout moment.  
  
 L’objet **état** propriété peut avoir une combinaison de valeurs. Par exemple, si une instruction est en cours d’exécution, cette propriété aura une valeur combinée de **adStateOpen** et **adStateExecuting**.  
  
 Le **état** propriété est en lecture seule.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>Voir aussi  
 [ConnectionString, ConnectionTimeout et les propriétés State, exemple (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout et les propriétés State, exemple (VC ++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
