---
description: PositionEnum
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
ms.openlocfilehash: 2d7b443e94f3bea5977aeaf953e84c66c826daeb
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88773168"
---
# <a name="positionenum"></a>PositionEnum
Spécifie la position actuelle du pointeur d’enregistrement dans un [Recordset](./recordset-object-ado.md).  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|Indique que le pointeur d’enregistrement actif se trouve sur BOF (autrement dit, la propriété [BOF](./bof-eof-properties-ado.md) a la **valeur true**).|  
|**adPosEOF**|-3|Indique que le pointeur d’enregistrement actif se trouve dans EOF (c’est-à-dire que la propriété [EOF](./bof-eof-properties-ado.md) a la **valeur true**).|  
|**adPosUnknown**|-1|Indique que le **jeu d’enregistrements** est vide, que la position actuelle est inconnue ou que le fournisseur ne prend pas en charge la propriété [AbsolutePage](./absolutepage-property-ado.md) ou [AbsolutePosition](./absoluteposition-property-ado.md) .|  
  
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
        [AbsolutePage, propriété (ADO)](./absolutepage-property-ado.md)  
    :::column-end:::
    :::column:::
        [AbsolutePosition, propriété (ADO)](./absoluteposition-property-ado.md)  
    :::column-end:::
:::row-end:::