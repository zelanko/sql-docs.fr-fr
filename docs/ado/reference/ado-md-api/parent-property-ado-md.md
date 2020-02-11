---
title: Propriété Parent (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parent
- Member::Parent
helpviewer_keywords:
- Parent property [ADO MD]
ms.assetid: 32c278c1-d8e1-4bb7-9ecd-2fbfdffee34b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2f6d6e03dd3288a5b0ca71bb9e129e1a57abf7c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949328"
---
# <a name="parent-property-ado-md"></a>Parent, propriété (ADO MD)
Indique le membre qui est le parent du [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) actuel dans une hiérarchie.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un objet [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Un membre qui se trouve au niveau supérieur d’une hiérarchie (la racine) n’a pas de parent. Cette propriété est prise en charge uniquement sur les objets **membres** appartenant à un objet de [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) . Une erreur se produit quand cette propriété est référencée à partir d’objets **membres** appartenant à un objet [position](../../../ado/reference/ado-md-api/position-object-ado-md.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Children, propriété (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)
