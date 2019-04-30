---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01f423652f32b9afe801ef99e299f65a6a860a8a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63314833"
---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
Spécifie si le [paramètre](../../../ado/reference/ado-api/parameter-object.md) représente un paramètre d’entrée, un paramètre de sortie, à la fois une entrée et un paramètre de sortie, ou la valeur de retour d’une procédure stockée.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adParamInput**|1|Valeur par défaut. Indique que le paramètre représente un paramètre d’entrée.|  
|**adParamInputOutput**|3|Indique que le paramètre représente un paramètre d’entrée et de sortie.|  
|**adParamOutput**|2|Indique que le paramètre représente un paramètre de sortie.|  
|**adParamReturnValue**|4|Indique que le paramètre représente une valeur de retour.|  
|**adParamUnknown**|0|Indique que la direction du paramètre est inconnue.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.ParameterDirection.INPUT|  
|AdoEnums.ParameterDirection.INPUTOUTPUT|  
|AdoEnums.ParameterDirection.OUTPUT|  
|AdoEnums.ParameterDirection.RETURNVALUE|  
|AdoEnums.ParameterDirection.UNKNOWN|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[CreateParameter, méthode (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|[Direction, propriété](../../../ado/reference/ado-api/direction-property.md)|
