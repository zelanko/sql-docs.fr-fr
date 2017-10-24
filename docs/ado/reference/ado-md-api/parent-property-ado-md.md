---
title: "Parent, propriété (ADO MD) | Documents Microsoft"
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
- Parent
- Member::Parent
helpviewer_keywords:
- Parent property [ADO MD]
ms.assetid: 32c278c1-d8e1-4bb7-9ecd-2fbfdffee34b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: baee402a130847f732583db8de376c120acb1bfb
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="parent-property-ado-md"></a>Parent, propriété (ADO MD)
Indique le membre qui est le parent d’actuel [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) dans une hiérarchie.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) de l’objet et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Un membre qui est au niveau supérieur d’une hiérarchie (racine) a aucun parent. Cette propriété est prise en charge uniquement sur **membre** objets appartenant à un [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) objet. Une erreur se produit lorsque cette propriété est référencée à partir de **membre** objets appartenant à un [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) objet.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet de membre (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Enfants, propriété (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)

