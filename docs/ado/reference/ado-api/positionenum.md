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
ms.openlocfilehash: d5f7ca47177a953313ff983bb25f9178b73b4930
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917605"
---
# <a name="positionenum"></a>PositionEnum
Spécifie la position actuelle du pointeur d’enregistrement dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Constant|Value|Description|  
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
  
|||  
|-|-|  
|[AbsolutePage, propriété (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)|[AbsolutePosition, propriété (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|
