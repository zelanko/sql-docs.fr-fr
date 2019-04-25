---
title: Écrire la méthode | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 52561b6d240a58e59490d607c8729b5d878b96a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642430"
---
# <a name="write-method"></a>Write, méthode
Écrit des données binaires à un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Buffer*  
 Un **Variant** qui contient un tableau d’octets à écrire.  
  
## <a name="remarks"></a>Notes  
 Octets spécifiés sont écrits dans le **Stream** objet sans espaces insérés entre chaque octet.  
  
 Actuel [Position](../../../ado/reference/ado-api/position-property-ado.md) est définie par l’octet suivant les données écrites. Le **écrire** méthode ne tronque pas le reste des données dans un flux de données. Si vous souhaitez tronquer ces octets, appelez [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Si vous écrivez après actuel [EOS](../../../ado/reference/ado-api/eos-property.md) position, la [taille](../../../ado/reference/ado-api/size-property-ado-stream.md) de la **Stream** augmente pour contenir les nouveaux octets, et **EOS** déplacera pour le nouveau dernier octet de la **Stream**.  
  
> [!NOTE]
>  Le **écrire** méthode est utilisée avec des flux binaires ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeBinary**). Pour les flux de texte (**Type** est **adTypeText**), utilisez [WriteText](../../../ado/reference/ado-api/writetext-method.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [WriteText, méthode](../../../ado/reference/ado-api/writetext-method.md)
