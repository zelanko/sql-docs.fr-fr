---
title: Type de propriété (flux ADO) | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Type
- _Stream::get_Type
- _Stream::put_Type
helpviewer_keywords:
- Type property [ADO Stream]
ms.assetid: f6a17e8c-7a28-48d0-bded-76b9e0cf7639
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50d0dc9e59c3ff47f3de9cee33349b85a94ecc8c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="type-property-ado-stream"></a>Type, propriété (ADO Stream)
Indique le type de données contenues dans le [flux](../../../ado/reference/ado-api/stream-object-ado.md) (binaire ou texte).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md) valeur qui spécifie le type de données contenues dans le **flux** objet. La valeur par défaut est **adTypeText**. Toutefois, si les données binaires sont initialement écrites dans un nouveau, vide **flux**, le **Type** sera modifiée en **adTypeBinary**.  
  
## <a name="remarks"></a>Notes  
 Le **Type** propriété est en lecture/écriture uniquement lorsque la position actuelle est au début de la **flux** ([Position](../../../ado/reference/ado-api/position-property-ado.md) est 0) et en lecture seule à toute autre position.  
  
 Le**Type** propriété détermine les méthodes devant être utilisées pour lire et écrire le **flux**. Pour le texte **flux**, utilisez [ReadText](../../../ado/reference/ado-api/readtext-method.md) et [WriteText](../../../ado/reference/ado-api/writetext-method.md). Fichier binaire **flux**, utilisez [en lecture](../../../ado/reference/ado-api/read-method.md) et [écrire](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [RecordType, propriété (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type, propriété (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
