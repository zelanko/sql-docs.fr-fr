---
title: "Description, propriété (ADO MD) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Member::Description
- Level::Description
- CubeDef::Description
- Hierarchy::Description
- Description
- Dimension::Description
helpviewer_keywords:
- Description property [ADO MD]
ms.assetid: 6d626d35-0bf3-4f24-9934-ad9c9c91273a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5bc33e6d2e82fc2b74fba7e250cc0b0fd3307ea2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="description-property-ado-md"></a>Description, propriété (ADO MD)
Retourne une description de texte de l’objet actuel.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **chaîne** et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Pour [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) objets, **Description** s’applique uniquement aux membres de formule et de mesure. **Description** retourne une chaîne vide (« ») pour tous les autres types de membres. Pour plus d’informations sur les différents types de membres, consultez la [Type](../../../ado/reference/ado-md-api/type-property-ado-md.md) propriété.  
  
 Cette propriété est uniquement prise en charge sur **membre** les objets qui appartiennent à un [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) objet. Une erreur se produit lorsque cette propriété est référencée à partir de **membre** objets appartenant à un [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) objet.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[CubeDef, objet (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|[Objet de dimension (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Objet de hiérarchie (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|  
|[Objet de niveau (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|[Objet de membre (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)||

