---
title: Propriété Children (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member::Children
- Children
helpviewer_keywords:
- Children property [ADO MD]
ms.assetid: 61d36468-1ccd-467a-9cb5-17d0bfacc766
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cbec9733044127d23e75364697a41ccd7e8910e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67911519"
---
# <a name="children-property-ado-md"></a>Children, propriété (ADO MD)
Retourne une collection de [membres](../../../ado/reference/ado-md-api/members-collection-ado-md.md) pour laquelle le [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) actuel est le parent dans la hiérarchie.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne une collection de **membres** et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 La propriété **Children** contient une collection de **membres** pour laquelle le **membre** actuel est le parent hiérarchique. Les objets **membres** de niveau feuille n’ont pas de membres enfants dans la collection **members** . Cette propriété est uniquement prise en charge sur les objets **membres** appartenant à un objet de [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) . Une erreur se produit quand cette propriété est référencée à partir d’objets **membres** appartenant à un objet [position](../../../ado/reference/ado-md-api/position-object-ado-md.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ChildCount, propriété (ADO MD)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
