---
description: StreamReadEnum
title: StreamReadEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
author: rothja
ms.author: jroth
ms.openlocfilehash: c0a0e8d93742574e9a2975b99d15c18500684e60
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777178"
---
# <a name="streamreadenum"></a>StreamReadEnum
Spécifie si l’intégralité du flux ou la ligne suivante doit être lue à partir d’un objet de [flux](./stream-object-ado.md) .  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|Par défaut. Lit tous les octets du flux, à partir de la position actuelle jusqu’au marqueur [EOS](./eos-property.md) . Il s’agit de la seule valeur **StreamReadEnum** valide avec des flux binaires ([type](./type-property-ado-stream.md) **adTypeBinary**).|  
|**adReadLine**|-2|Lit la ligne suivante dans le flux (désigné par la propriété [LineSeparator](./lineseparator-property-ado.md) ).|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Read, méthode](./read-method.md)  
    :::column-end:::
    :::column:::
        [ReadText, méthode](./readtext-method.md)  
    :::column-end:::
:::row-end:::