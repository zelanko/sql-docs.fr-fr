---
title: "Enfants, propriété (ADO MD) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Member::Children
- Children
helpviewer_keywords: Children property [ADO MD]
ms.assetid: 61d36468-1ccd-467a-9cb5-17d0bfacc766
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bf9b0ca151408a1f1e66a7a77f98ea824f6b468f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="children-property-ado-md"></a>Enfants, propriété (ADO MD)
Retourne un [membres](../../../ado/reference/ado-md-api/members-collection-ado-md.md) collection pour laquelle actuel [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) est le parent dans la hiérarchie.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **membres** collection et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Le **enfants** propriété contient un **membres** collection pour laquelle actuel **membre** est le parent hiérarchique. Niveau de feuille **membre** objets n’ont aucun membre enfant le **membres** collection. Cette propriété est uniquement prise en charge sur **membre** objets appartenant à un [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) objet. Une erreur se produit lorsque cette propriété est référencée à partir de **membre** objets appartenant à un [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) objet.  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ChildCount, propriété (ADO MD)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
