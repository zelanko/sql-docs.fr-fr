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
ms.openlocfilehash: 1aa8ff80f02d84aaa69904d914e0e40da44da930
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441811"
---
# <a name="streamreadenum"></a>StreamReadEnum
Spécifie si l’intégralité du flux ou la ligne suivante doit être lue à partir d’un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|Par défaut. Lit tous les octets du flux, à partir de la position actuelle jusqu’au marqueur [EOS](../../../ado/reference/ado-api/eos-property.md) . Il s’agit de la seule valeur **StreamReadEnum** valide avec des flux binaires ([type](../../../ado/reference/ado-api/type-property-ado-stream.md) **adTypeBinary**).|  
|**adReadLine**|-2|Lit la ligne suivante dans le flux (désigné par la propriété [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) ).|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Read, méthode](../../../ado/reference/ado-api/read-method.md)  
    :::column-end:::
    :::column:::
        [ReadText, méthode](../../../ado/reference/ado-api/readtext-method.md)  
    :::column-end:::
:::row-end:::
