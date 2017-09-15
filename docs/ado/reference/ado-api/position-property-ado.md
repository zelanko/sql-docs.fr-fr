---
title: "Position, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::Position
helpviewer_keywords:
- Position property [ADO]
ms.assetid: daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 76a3d94b97fa32e372cd6cc67367450d2f62530b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="position-property-ado"></a>Position, propriété (ADO)
Indique la position actuelle dans un [flux](../../../ado/reference/ado-api/stream-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Long** valeur qui spécifie le décalage, en octets, de la position actuelle à partir du début du flux de données. La valeur par défaut est 0, qui représente le premier octet dans le flux de données.  
  
## <a name="remarks"></a>Notes  
 La position actuelle peut être déplacée vers un point après la fin du flux de données. Si vous spécifiez la position actuelle au-delà de la fin du flux, le [taille](../../../ado/reference/ado-api/size-property-ado-stream.md) de la **flux** objet augmente en conséquence. Les nouveaux octets ajoutés de cette façon est null.  
  
> [!NOTE]
>  **Position** mesure toujours des octets. Pour les flux de texte à l’aide de jeux de caractères multioctets, multipliez la position par la taille de caractères pour déterminer le nombre de caractères. Par exemple, pour un jeu de caractères codés sur deux, le premier caractère est à la position 0, le deuxième caractère à la position 2, le troisième caractère à la position 4 et ainsi de suite.  
  
> [!NOTE]
>  Les valeurs négatives ne peut pas être utilisés pour modifier la position actuelle dans un **flux**. Seuls les nombres positifs peuvent être utilisés pour **Position**.  
  
> [!NOTE]
>  Pour en lecture seule **flux** ADO ne renvoie pas une erreur si des objets **Position** est défini sur une valeur supérieure à la **taille** de la **flux**. Cela ne modifie pas la taille de la **flux**, ou modifiez la **flux** contenu. Toutefois, cela doit être évité, car il en résulte un sans signification **Position**valeur.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet de flux de données (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu de caractères, propriété (ADO)](../../../ado/reference/ado-api/charset-property-ado.md)
