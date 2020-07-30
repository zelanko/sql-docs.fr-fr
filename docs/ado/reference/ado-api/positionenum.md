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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6a61dae9888628302da3326a1465f4182c49e39c
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243220"
---
# <a name="positionenum"></a>PositionEnum
Spécifie la position actuelle du pointeur d’enregistrement dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|Indique que le pointeur d’enregistrement actif se trouve sur BOF (autrement dit, la propriété [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) a la **valeur true**).|  
|**adPosEOF**|-3|Indique que le pointeur d’enregistrement actif se trouve dans EOF (c’est-à-dire que la propriété [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) a la **valeur true**).|  
|**adPosUnknown**|-1|Indique que le **jeu d’enregistrements** est vide, que la position actuelle est inconnue ou que le fournisseur ne prend pas en charge la propriété [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) ou [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) .|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.Position.BOF|  
|AdoEnums. position. EOF|  
|AdoEnums. position. Unknown|  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [AbsolutePage, propriété (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)  
    :::column-end:::
    :::column:::
        [AbsolutePosition, propriété (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)  
    :::column-end:::
:::row-end:::
