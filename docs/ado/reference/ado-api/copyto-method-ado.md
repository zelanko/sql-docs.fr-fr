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
ms.openlocfilehash: 25d57116e1fa24658d62a0c9083e00a3e320d2a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933371"
---
# <a name="copyto-method-ado"></a>CopyTo, méthode (ADO)
Copie le nombre spécifié de caractères ou d’octets (selon le [type](../../../ado/reference/ado-api/type-property-ado-stream.md)) dans le [flux](../../../ado/reference/ado-api/stream-object-ado.md) vers un autre objet de **flux** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.CopyTo DestStream, NumChars  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DestStream*  
 Valeur de variable objet qui contient une référence à un objet de **flux** ouvert. Le **flux** actuel est copié dans le **flux** de destination spécifié par *DestStream*. Le **flux** de destination doit déjà être ouvert. Si ce n’est pas le cas, une erreur d’exécution se produit.  
  
> [!NOTE]
>  Le paramètre *DestStream* ne peut pas être un proxy d’objet de **flux** , car cela nécessite l’accès à une interface privée sur l’objet de **flux** qui ne peut pas être à distance au client.  
  
 *NumChars*  
 facultatif. Valeur **entière** qui spécifie le nombre d’octets ou de caractères à copier à partir de la position actuelle dans le **flux** source dans le **flux**de destination. La valeur par défaut est-1, qui spécifie que tous les caractères ou octets sont copiés de la position actuelle vers [EOS](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Notes  
 Cette méthode copie le nombre spécifié de caractères ou d’octets, en commençant à la position actuelle spécifiée par la propriété [position](../../../ado/reference/ado-api/position-property-ado.md) . Si le nombre spécifié est supérieur au nombre d’octets disponibles jusqu’à **EOS**, seuls les caractères ou octets de la position actuelle vers **EOS** sont copiés. Si la valeur de *NUMCHARS* est-1, ou si elle est omise, tous les caractères ou octets à partir de la position actuelle sont copiés.  
  
 S’il existe des caractères ou des octets dans le flux de destination, tout le contenu au-delà du point où la copie se termine reste et n’est pas tronqué. **Position** devient l’octet qui suit immédiatement le dernier octet copié. Si vous souhaitez tronquer ces octets, appelez [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 **CopyTo** doit être utilisé pour copier des données vers un **flux** de destination du même type que le **flux** source (leurs paramètres de propriété de **type** sont à la fois **adTypeText** ou **adTypeBinary**). Pour les objets de **flux** de texte, vous pouvez modifier le paramètre de propriété [charset](../../../ado/reference/ado-api/charset-property-ado.md) du **flux** de destination pour effectuer la conversion d’un jeu de caractères à un autre. En outre, les objets de **flux** de texte peuvent être copiés avec succès dans des objets de flux binaires, mais les objets de **flux** binaire ne peuvent pas être copiés dans **des objets de** **flux** de texte.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
