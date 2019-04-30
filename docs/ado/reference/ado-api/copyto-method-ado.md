---
title: CopyTo, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_CopyTo
- _Stream::CopyTo
helpviewer_keywords:
- CopyTo method [ADO]
ms.assetid: b4aa5714-916b-48b8-8b09-cc2708379602
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01b2e7dc8b70c109fc6cf998cec2bbad1147692c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63308906"
---
# <a name="copyto-method-ado"></a>CopyTo, méthode (ADO)
Copie le nombre spécifié de caractères ou d’octets (en fonction de [Type](../../../ado/reference/ado-api/type-property-ado-stream.md)) dans le [Stream](../../../ado/reference/ado-api/stream-object-ado.md) vers un autre **Stream** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.CopyTo DestStream, NumChars  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DestStream*  
 Valeur de variable objet qui contient une référence à une ouverture **Stream** objet. Actuel **Stream** est copié vers la destination **Stream** spécifié par *DestStream*. La destination **Stream** doit déjà être ouvert. Dans le cas contraire, une erreur d’exécution se produit.  
  
> [!NOTE]
>  Le *DestStream* paramètre ne peut pas être un proxy de **Stream** de l’objet, car cela nécessite un accès à une interface privée sur le **Stream** objet ne peut pas être exécutée à distance sur le client.  
  
 *NumChars*  
 Facultatif. Un **entier** valeur qui spécifie le nombre d’octets ou de caractères à copier à partir de la position actuelle dans la source **Stream** vers la destination **Stream**. La valeur par défaut est -1, qui spécifie que tous les caractères ou octets sont copiés à partir de la position actuelle pour [EOS](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Notes  
 Cette méthode copie le nombre spécifié de caractères ou d’octets à partir de la position actuelle spécifiée par le [Position](../../../ado/reference/ado-api/position-property-ado.md) propriété. Si le nombre spécifié est supérieur au nombre d’octets jusqu'à disponible **EOS**, puis uniquement des caractères ou octets à partir de la position actuelle pour **EOS** sont copiés. Si la valeur de *NumChars* est -1, ou est omis, tous les caractères ou octets à partir de la position actuelle sont copiés.  
  
 S’il existe des caractères ou octets dans le flux de destination, tout le contenu au-delà du point où se termine la copie reste et n’est pas tronqué. **Position** devient l’octet suivant immédiatement le dernier octet copié. Si vous souhaitez tronquer ces octets, appelez [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 **CopyTo** doit être utilisé pour copier des données vers une destination **Stream** du même type que la source **Stream** (leurs **Type** paramètres de propriété sont les deux **adTypeText** ou les deux **adTypeBinary**). Pour le texte **Stream** objets, vous pouvez modifier le [Charset](../../../ado/reference/ado-api/charset-property-ado.md) paramètre de propriété de la destination **Stream** permet de convertir un jeu de caractères à un autre. En outre, le texte **Stream** objets peuvent être copiés avec succès en binaire **Stream** objets mais binaire **Stream** objets ne peut pas être copiés dans le texte **Stream**  objets.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
