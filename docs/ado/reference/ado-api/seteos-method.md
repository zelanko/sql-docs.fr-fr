---
description: SetEOS, méthode
title: SetEos, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ffe6f7d4a8861fb58f3b72f2b75de3de1ac9736
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777488"
---
# <a name="seteos-method"></a>SetEOS, méthode
Définit la position qui correspond à la fin du flux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Notes  
 **SetEOS** met à jour la valeur de la propriété [EOS](./eos-property.md) , en mettant la [position](./position-property-ado.md) actuelle à la fin du flux. Tous les octets ou caractères qui suivent la position actuelle sont tronqués.  
  
 Comme [Write](./write-method.md), [WRITETEXT](./writetext-method.md)et [CopyTo](./copyto-method-ado.md) ne tronquent pas de valeurs supplémentaires dans les objets de **flux** existants, vous pouvez tronquer ces octets ou caractères en définissant la nouvelle position de fin de flux avec **SetEOS**.  
  
> [!CAUTION]
>  Si vous affectez à **EOS** une position avant la fin réelle du flux, vous perdrez toutes les données après la nouvelle position **EOS** .  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](./stream-object-ado.md)