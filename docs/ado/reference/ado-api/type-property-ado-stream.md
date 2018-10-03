---
title: Type de propriété (ADO Stream) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Type
- _Stream::get_Type
- _Stream::put_Type
helpviewer_keywords:
- Type property [ADO Stream]
ms.assetid: f6a17e8c-7a28-48d0-bded-76b9e0cf7639
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e4df670c5fe6ca42015e7e85445dafde47738f1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637037"
---
# <a name="type-property-ado-stream"></a>Type, propriété (objet Stream ADO)
Indique le type de données contenues dans le [Stream](../../../ado/reference/ado-api/stream-object-ado.md) (binaire ou texte).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md) valeur qui spécifie le type de données contenues dans le **Stream** objet. La valeur par défaut est **adTypeText**. Toutefois, si les données binaires sont initialement écrits dans un nouveau, vide **Stream**, le **Type** sera modifiée en **adTypeBinary**.  
  
## <a name="remarks"></a>Notes  
 Le **Type** propriété est en lecture/écriture uniquement lorsque la position actuelle est au début de la **Stream** ([Position](../../../ado/reference/ado-api/position-property-ado.md) est 0) et en lecture seule à n’importe quel autre position.  
  
 Le**Type** propriété détermine quelles méthodes doivent être utilisés pour lire et écrire le **Stream**. Pour le texte **flux**, utilisez [ReadText](../../../ado/reference/ado-api/readtext-method.md) et [WriteText](../../../ado/reference/ado-api/writetext-method.md). Pour le fichier binaire **flux**, utilisez [en lecture](../../../ado/reference/ado-api/read-method.md) et [écrire](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [RecordType, propriété (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type, propriété (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
