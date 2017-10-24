---
title: "Size, propriété (flux ADO) | Documents Microsoft"
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
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c5a4027bf589a469092a6605743df3d08147e7d2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

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
 [Objet de flux de données (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété Size (paramètre ADO)](../../../ado/reference/ado-api/size-property-ado-parameter.md)

