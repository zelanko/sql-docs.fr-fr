---
title: PositionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PositionEnum
helpviewer_keywords:
- PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21a2ea98ea4592d9900cd9623502a8d918b34c9b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47774187"
---
# <a name="positionenum"></a>PositionEnum
Spécifie la position actuelle du pointeur d’enregistrement au sein d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|Indique que le pointeur d’enregistrement actuel est de type BOF (autrement dit, le [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) propriété est **True**).|  
|**adPosEOF**|-3|Indique que le pointeur d’enregistrement actuel est de type EOF (autrement dit, le [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) propriété est **True**).|  
|**adPosUnknown**|-1|Indique que le **Recordset** est vide, la position actuelle est inconnue ou le fournisseur ne prend pas en charge la [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) ou [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) propriété.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
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
