---
description: ObjectStateEnum
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
ms.openlocfilehash: 0c387240e36225f03c8ba1287618ab59a98fb63c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443021"
---
# <a name="objectstateenum"></a>ObjectStateEnum
Spécifie si un objet est ouvert ou fermé, s’il se connecte à une source de données, exécute une commande ou récupère des données.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adStateClosed**|0|Indique que l’objet est fermé.|  
|**adStateOpen**|1|Indique que l’objet est ouvert.|  
|**adStateConnecting**|2|Indique que l’objet se connecte.|  
|**adStateExecuting**|4|Indique que l’objet exécute une commande.|  
|**adStateFetching**|8|Indique que les lignes de l’objet sont en cours de récupération.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constante|  
|--------------|  
|AdoEnums.ObjectState.CLOSED|  
|AdoEnums.ObjectState.OPEN|  
|AdoEnums.ObjectState.CONNECTING|  
|AdoEnums.ObjectState.EXECUTING|  
|AdoEnums.ObjectState.FETCHING|  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [State, propriété (ADO)](../../../ado/reference/ado-api/state-property-ado.md)  
    :::column-end:::
    :::column:::
        [State, propriété (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)  
    :::column-end:::
:::row-end:::
