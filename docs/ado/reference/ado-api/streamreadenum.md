---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 37d2ba0834d2a4469d97a36f39677f407a5e61be
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66710674"
---
# <a name="streamreadenum"></a>StreamReadEnum
Spécifie si l’ensemble du flux ou la ligne suivante doit être lue à partir d’un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|Valeur par défaut. Lit tous les octets dans le flux, à partir de la position actuelle et les versions ultérieures à la [EOS](../../../ado/reference/ado-api/eos-property.md) marqueur. Cette option est uniquement valide **StreamReadEnum** valeur avec des flux binaires ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeBinary**).|  
|**adReadLine**|-2|Lit la ligne suivante à partir du flux (désigné par le [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) propriété).|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Read, méthode](../../../ado/reference/ado-api/read-method.md)|[ReadText, méthode](../../../ado/reference/ado-api/readtext-method.md)|
