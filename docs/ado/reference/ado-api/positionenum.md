---
title: PositionEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: PositionEnum
helpviewer_keywords: PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 006958663621ec4d226f756af6aad44c05f5a92e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="positionenum"></a>PositionEnum
Spécifie la position actuelle du pointeur d’enregistrement dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|Indique que le pointeur d’enregistrement actif est de type BOF (autrement dit, le [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) propriété **True**).|  
|**adPosEOF**|-3|Indique que le pointeur d’enregistrement actif est de type EOF (autrement dit, le [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) propriété **True**).|  
|**adPosUnknown**|-1|Indique que le **Recordset** est vide, la position actuelle est inconnue ou le fournisseur ne prend pas en charge la [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) ou [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) propriété.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.Position.BOF|  
|AdoEnums.Position.EOF|  
|AdoEnums.Position.UNKNOWN|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[AbsolutePage, propriété (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)|[AbsolutePosition, propriété (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|
