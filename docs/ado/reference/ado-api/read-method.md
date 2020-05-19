---
title: Read, méthode | Microsoft Docs
ms.prod: sql
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 75b39b758d48a173bcfbe84e3fecbd20cce5ee12
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82754268"
---
# <a name="read-method"></a>Read, méthode
Lit un nombre spécifié d’octets à partir d’un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *NumBytes*  
 facultatif. Valeur de **type long** qui spécifie le nombre d’octets à lire dans le fichier ou la valeur [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) **adReadAll**, qui est la valeur par défaut.  
  
## <a name="return-value"></a>Valeur renvoyée  
 La méthode **Read** lit un nombre spécifié d’octets ou le flux entier à partir d’un objet de **flux** et retourne les données résultantes sous la forme d’un **Variant**.  
  
## <a name="remarks"></a>Notes  
 Si *NumBytes* est supérieur au nombre d’octets restants dans le **flux**, seuls les octets restants sont retournés. Les données lues ne sont pas complétées pour correspondre à la longueur spécifiée par *NumBytes*. S’il n’y a pas d’octets à lire, un variant avec une valeur null est retourné. La **lecture** ne peut pas être utilisée pour lire vers l’arrière.  
  
> [!NOTE]
>  *NumBytes* mesure toujours les octets. Pour les objets de **flux** de texte ([type](../../../ado/reference/ado-api/type-property-ado-stream.md) **adTypeText**), utilisez [READTEXT](../../../ado/reference/ado-api/readtext-method.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ReadText, méthode](../../../ado/reference/ado-api/readtext-method.md)
