---
title: Enfants, propriété (ADO MD) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: f489a87573dabbd091f5d2dce8a084b53cc5771e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626127"
---
# <a name="children-property-ado-md"></a>Children, propriété (ADO MD)
Retourne un [membres](../../../ado/reference/ado-md-api/members-collection-ado-md.md) collection pour laquelle actuel [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) est le parent dans la hiérarchie.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **membres** collection et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Le **enfants** propriété contient un **membres** collection pour laquelle actuel **membre** est le parent hiérarchique. Les terminaux de niveau **membre** objets n’ont aucun membre enfant le **membres** collection. Cette propriété est uniquement pris en charge **membre** objets appartenant à un [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) objet. Une erreur se produit lorsque cette propriété est référencée à partir de **membre** objets appartenant à un [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) objet.  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ChildCount, propriété (ADO MD)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
