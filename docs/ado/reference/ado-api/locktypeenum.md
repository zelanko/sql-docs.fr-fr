---
title: LockTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bcd2e4d2a3b84ef913954c1a1a2d7fa76393040c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864072"
---
# <a name="locktypeenum"></a>LockTypeEnum
Spécifie le type de verrou placé sur les enregistrements pendant la modification.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|Indique les mises à jour par lot optimiste. Requis pour le mode de mise à jour par lots.|  
|**adLockOptimistic**|3|Indique le verrouillage optimiste, enregistrement par enregistrement. Le fournisseur utilise le verrouillage optimiste, verrouillage lorsque vous appelez le [mise à jour](../../../ado/reference/ado-api/update-method.md) (méthode).|  
|**adLockPessimistic**|2|Indique un verrouillage pessimiste, enregistrement par enregistrement. Le fournisseur effectue ce qui est nécessaire pour garantir la réussite l’édition des enregistrements, généralement par un verrouillage d’enregistrements à la source de données immédiatement après la modification.|  
|**adLockReadOnly**|1|Indique les enregistrements en lecture seule. Vous ne pouvez pas modifier les données.|  
|**adLockUnspecified**|-1|Ne spécifie pas un type de verrou. Pour les clones, le clone est créé avec le même type de verrou que l’original.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.LockType.BATCHOPTIMISTIC|  
|AdoEnums.LockType.OPTIMISTIC|  
|AdoEnums.LockType.PESSIMISTIC|  
|AdoEnums.LockType.READONLY|  
|AdoEnums.LockType.UNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Clone, méthode (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[LockType, propriété (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[WillExecute, événement (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
