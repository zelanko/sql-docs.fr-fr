---
title: Read, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Stream::raw_Read
- _Stream::Read
helpviewer_keywords:
- Read method [ADO]
ms.assetid: 838502de-80f1-4eeb-8838-dd3d9403e567
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f4594e4b85ad66b1ab11a2966bc7a0d79815db09
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702972"
---
# <a name="read-method"></a>Read, méthode
Lit un nombre spécifié d’octets à partir d’un fichier binaire [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *NumBytes*  
 Facultatif. Un **Long** valeur qui spécifie le nombre d’octets à lire à partir du fichier ou le [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) valeur **adReadAll**, qui est la valeur par défaut.  
  
## <a name="return-value"></a>Valeur de retour  
 Le **en lecture** méthode lit un nombre spécifié d’octets ou l’intégralité du flux à partir d’un **Stream** de l’objet et retourne les données résultantes comme un **Variant**.  
  
## <a name="remarks"></a>Notes  
 Si *NumBytes* est supérieur au nombre d’octets restant dans le **Stream**, seuls les octets restants sont retournés. La lecture de données ne sont pas remplies pour correspondre à la longueur spécifiée par *NumBytes*. S’il n’y a aucun octet restant à lire, une variante avec une valeur null est retournée. **Lecture** ne peut pas être utilisé pour lire vers l’arrière.  
  
> [!NOTE]
>  *NbOctets* mesure toujours des octets. Pour le texte **Stream** objets ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**), utilisez [ReadText](../../../ado/reference/ado-api/readtext-method.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ReadText, méthode](../../../ado/reference/ado-api/readtext-method.md)
