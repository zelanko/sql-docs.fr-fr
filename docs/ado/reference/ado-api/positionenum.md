---
title: PositionEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- PositionEnum
helpviewer_keywords:
- PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c3f317b92d138f020a43f26d71cbadd0f0cd412e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

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

