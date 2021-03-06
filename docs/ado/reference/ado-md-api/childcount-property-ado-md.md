---
description: ChildCount, propriété (ADO MD)
title: Propriété ChildCount (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ChildCount
- Member::ChildCount
helpviewer_keywords:
- ChildCount property [ADO MD]
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
author: rothja
ms.author: jroth
ms.openlocfilehash: a5c3668a115de8137cd96f489f3e11483cb50045
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987130"
---
# <a name="childcount-property-ado-md"></a>ChildCount, propriété (ADO MD)
Indique le nombre de membres pour lesquels l’objet [membre](./member-object-ado-md.md) actuel est le parent dans une hiérarchie.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un entier **long** et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **ChildCount** pour retourner une estimation du nombre d’enfants d’un **membre** . Les enfants réels d’un **membre** peuvent être retournés par la propriété [Children](./children-property-ado-md.md) .  
  
 Pour les objets **membres** d’un objet [position](./position-object-ado-md.md) , le nombre maximal retourné est 65536. Si le nombre réel d’enfants dépasse 65536, la valeur retournée sera toujours 65536. Par conséquent, l’application doit interpréter un **ChildCount** de 65536 en tant que supérieur ou égal à 65536 enfants.  
  
 Pour les objets **membres** d’un objet [Level](./level-object-ado-md.md) , utilisez la propriété ADO collection [Count](../ado-api/count-property-ado.md) sur la collection **Children** pour déterminer le nombre exact d’enfants. La détermination du nombre exact d’enfants peut être lente si le nombre d’enfants dans la collection est important.  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](./member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété Children (ADO MD)](./children-property-ado-md.md)   
 [Count, propriété (ADO)](../ado-api/count-property-ado.md)   
 [Members, collection (ADO MD)](./members-collection-ado-md.md)