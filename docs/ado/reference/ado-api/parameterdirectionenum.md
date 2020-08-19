---
description: ParameterDirectionEnum
title: ParameterDirectionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ParameterDirectionEnum
helpviewer_keywords:
- ParameterDirectionEnum enumeration [ADO]
ms.assetid: c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c586b4e7ce2e18411d147e8aafb4eb144e01e6f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442781"
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Spécifie si le [paramètre](../../../ado/reference/ado-api/parameter-object.md) représente un paramètre d’entrée, un paramètre de sortie, à la fois un paramètre d’entrée et un paramètre de sortie, ou la valeur de retour d’une procédure stockée.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adParamInput**|1|Par défaut. Indique que le paramètre représente un paramètre d’entrée.|  
|**adParamInputOutput**|3|Indique que le paramètre représente à la fois un paramètre d’entrée et un paramètre de sortie.|  
|**adParamOutput**|2|Indique que le paramètre représente un paramètre de sortie.|  
|**adParamReturnValue**|4|Indique que le paramètre représente une valeur de retour.|  
|**adParamUnknown**|0|Indique que la direction du paramètre est inconnue.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constante|  
|--------------|  
|AdoEnums.ParameterDirection.INPUT|  
|AdoEnums.ParameterDirection.INPUTOUTPUT|  
|AdoEnums. ParameterDirection. OUTPUT|  
|AdoEnums.ParameterDirection.RETURNVALUE|  
|AdoEnums.ParameterDirection.UNKNOWN|  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [CreateParameter, méthode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)  
    :::column-end:::
    :::column:::
        [Direction, propriété](../../../ado/reference/ado-api/direction-property.md)  
    :::column-end:::
:::row-end:::
