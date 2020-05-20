---
title: Write, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_Write
- _Stream::Write
helpviewer_keywords:
- Write method [ADO]
ms.assetid: 02982e6a-ac5f-4af2-b82e-ce12534b84b2
author: rothja
ms.author: jroth
ms.openlocfilehash: 911a9dfb21c054dc95c54d9fb429d628d8e01fa4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764430"
---
# <a name="write-method"></a>Write, méthode
Écrit des données binaires dans un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Mémoire tampon*  
 **Variant** qui contient un tableau d’octets à écrire.  
  
## <a name="remarks"></a>Remarques  
 Les octets spécifiés sont écrits dans l’objet de **flux** sans aucun espace intermédiaire entre chaque octet.  
  
 La [position](../../../ado/reference/ado-api/position-property-ado.md) actuelle est définie sur l’octet qui suit les données écrites. La méthode **Write** ne tronque pas le reste des données dans un flux. Si vous souhaitez tronquer ces octets, appelez [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Si vous écrivez après la position [EOS](../../../ado/reference/ado-api/eos-property.md) actuelle, la [taille](../../../ado/reference/ado-api/size-property-ado-stream.md) du **flux** sera augmentée pour contenir de nouveaux octets, et **EOS** passera au nouvel octet dernier dans le **flux**.  
  
> [!NOTE]
>  La méthode **Write** est utilisée avec les flux binaires (le[type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeBinary**). Pour les flux de texte (**type** **adTypeText**), utilisez [WRITETEXT](../../../ado/reference/ado-api/writetext-method.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [WriteText, méthode](../../../ado/reference/ado-api/writetext-method.md)
