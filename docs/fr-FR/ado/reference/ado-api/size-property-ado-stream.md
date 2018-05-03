---
title: Size, propriété (flux ADO) | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 67072d926e97728c53a41617dfc8152a0480f69b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="size-property-ado-stream"></a>Taille, propriété (flux ADO)
Indique la taille du flux en nombre d’octets.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **Long** valeur qui spécifie la taille du flux en nombre d’octets. La valeur par défaut est la taille de flux, ou -1 si la taille du flux de données n’est pas connue.  
  
## <a name="remarks"></a>Notes  
 **Taille** peut être utilisé uniquement avec ouverte [flux](../../../ado/reference/ado-api/stream-object-ado.md) objets.  
  
> [!NOTE]
>  N’importe quel nombre de bits peut être stocké dans un **flux** objet, limitée uniquement par les ressources système. Si le **flux** contient plus de bits peut être représenté par un **Long** valeur, **taille** est tronqué et par conséquent ne représentent pas avec précision la longueur de la **Flux**.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Size, propriété (paramètre ADO)](../../../ado/reference/ado-api/size-property-ado-parameter.md)
