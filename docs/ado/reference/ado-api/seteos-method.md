---
title: SetEOS, méthode | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0db8c7972d6b647cdd021d43dbb3cdee1ba0452
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678527"
---
# <a name="seteos-method"></a>SetEOS, méthode
Définit la position de la fin du flux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Notes  
 **SetEOS** met à jour la valeur de la [EOS](../../../ado/reference/ado-api/eos-property.md) propriété, en rendant actuel [Position](../../../ado/reference/ado-api/position-property-ado.md) la fin du flux. Tous les octets ou caractères qui suivent la position actuelle sont tronqués.  
  
 Étant donné que [écrire](../../../ado/reference/ado-api/write-method.md), [WriteText](../../../ado/reference/ado-api/writetext-method.md), et [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) ne tronquent aucune valeur supplémentaire existant **Stream** objets, vous pouvez tronquer ces octets ou caractères en définissant la nouvelle position de fin de flux avec **SetEOS**.  
  
> [!CAUTION]
>  Si vous définissez **EOS** à une position avant la fin du flux, vous perdrez toutes les données une fois que le nouvel **EOS** position.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
