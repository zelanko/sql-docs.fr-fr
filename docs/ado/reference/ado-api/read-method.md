---
description: Read, méthode
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
ms.openlocfilehash: 7c2b2b1579beb967ec75b5a0b32532b846640b01
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88772718"
---
# <a name="read-method"></a>Read, méthode
Lit un nombre spécifié d’octets à partir d’un objet de [flux](./stream-object-ado.md) binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *NumBytes*  
 facultatif. Valeur de **type long** qui spécifie le nombre d’octets à lire dans le fichier ou la valeur [StreamReadEnum](./streamreadenum.md) **adReadAll**, qui est la valeur par défaut.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode **Read** lit un nombre spécifié d’octets ou le flux entier à partir d’un objet de **flux** et retourne les données résultantes sous la forme d’un **Variant**.  
  
## <a name="remarks"></a>Notes  
 Si *NumBytes* est supérieur au nombre d’octets restants dans le **flux**, seuls les octets restants sont retournés. Les données lues ne sont pas complétées pour correspondre à la longueur spécifiée par *NumBytes*. S’il n’y a pas d’octets à lire, un variant avec une valeur null est retourné. La **lecture** ne peut pas être utilisée pour lire vers l’arrière.  
  
> [!NOTE]
>  *NumBytes* mesure toujours les octets. Pour les objets de **flux** de texte ([type](./type-property-ado-stream.md) **adTypeText**), utilisez [READTEXT](./readtext-method.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ReadText, méthode](./readtext-method.md)