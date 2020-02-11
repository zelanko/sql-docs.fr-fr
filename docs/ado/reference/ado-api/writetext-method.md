---
title: WriteText, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords:
- WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 64b7d8fd3f2220562e3695d6e31c83261daa2e60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947497"
---
# <a name="writetext-method"></a>WriteText, méthode
Écrit une chaîne de texte spécifiée dans un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Données*  
 Valeur de **chaîne** qui contient le texte en caractères à écrire.  
  
 *Options*  
 facultatif. Valeur de [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md) qui spécifie si un caractère de séparation de ligne doit être écrit à la fin de la chaîne spécifiée.  
  
## <a name="remarks"></a>Notes  
 Les chaînes spécifiées sont écrites dans l’objet de **flux** sans aucun espace ou caractère intermédiaire entre chaque chaîne.  
  
 La [position](../../../ado/reference/ado-api/position-property-ado.md) actuelle est définie sur le caractère qui suit les données écrites. La méthode **WRITETEXT** ne tronque pas le reste des données dans un flux. Si vous souhaitez tronquer ces caractères, appelez [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Si vous écrivez après la position [EOS](../../../ado/reference/ado-api/eos-property.md) actuelle, la [taille](../../../ado/reference/ado-api/size-property-ado-stream.md) du **flux** est augmentée pour contenir de nouveaux caractères, et **EOS** se déplace vers le nouvel octet dernier dans le **flux**.  
  
> [!NOTE]
>  La méthode **WRITETEXT** est utilisée avec les flux de texte (le[type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**). Pour les flux binaires (**type** **adTypeBinary**), utilisez [Write](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Write, méthode](../../../ado/reference/ado-api/write-method.md)
