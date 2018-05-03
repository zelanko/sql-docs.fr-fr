---
title: LockTypeEnum | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba3e63dffbac818f9be074deef15f598b8905aa9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="locktypeenum"></a>LockTypeEnum
Spécifie le type de verrou placé sur les enregistrements pendant la modification.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|Indique les mises à jour par lot optimiste. Requis pour le mode de mise à jour par lots.|  
|**adLockOptimistic**|3|Indique un verrouillage optimiste, enregistrement par enregistrement. Le fournisseur utilise le verrouillage optimiste, verrouiller des enregistrements uniquement quand vous appelez le [mise à jour](../../../ado/reference/ado-api/update-method.md) (méthode).|  
|**adLockPessimistic**|2|Indique un verrouillage pessimiste, enregistrement par enregistrement. Le fournisseur effectue ce qui est nécessaire pour garantir la réussite l’édition des enregistrements, généralement par un verrouillage des enregistrements de la source de données immédiatement après la modification.|  
|**adLockReadOnly**|1|Indique les enregistrements en lecture seule. Vous ne pouvez pas modifier les données.|  
|**adLockUnspecified**|-1|Ne spécifie pas un type de verrou. Pour les clones, le clone est créé avec le même type de verrou que l’original.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
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
