---
title: ObjectStateEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectStateEnum
helpviewer_keywords:
- ObjectStateEnum enumeration [ADO]
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
author: rothja
ms.author: jroth
ms.openlocfilehash: e0b69deb64cc4ea04c007fd3d3328cb4154cc3e8
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242616"
---
# <a name="objectstateenum"></a>ObjectStateEnum
Spécifie si un objet est ouvert ou fermé, s’il se connecte à une source de données, exécute une commande ou récupère des données.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adStateClosed**|0|Indique que l’objet est fermé.|  
|**adStateOpen**|1|Indique que l’objet est ouvert.|  
|**adStateConnecting**|2|Indique que l’objet se connecte.|  
|**adStateExecuting**|4|Indique que l’objet exécute une commande.|  
|**adStateFetching**|8|Indique que les lignes de l’objet sont en cours de récupération.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.ObjectState.CLOSED|  
|AdoEnums.ObjectState.OPEN|  
|AdoEnums.ObjectState.CONNECTING|  
|AdoEnums.ObjectState.EXECUTING|  
|AdoEnums.ObjectState.FETCHING|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|||

:::row:::
    :::column:::
        [State, propriété (ADO)](../../../ado/reference/ado-api/state-property-ado.md)  
    :::column-end:::
    :::column:::
        [State, propriété (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)  
    :::column-end:::
:::row-end:::
