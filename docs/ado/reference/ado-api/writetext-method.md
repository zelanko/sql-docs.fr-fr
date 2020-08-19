---
description: WriteText, méthode
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b561c8d798236fa0c6df262e2fc2db4c4729cb90
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441491"
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
