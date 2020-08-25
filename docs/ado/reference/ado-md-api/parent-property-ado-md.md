---
description: Parent, propriété (ADO MD)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 208fce5328f76f35cdd562ca82bb989851f366cb
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777908"
---
# <a name="parent-property-ado-md"></a>Parent, propriété (ADO MD)
Indique le membre qui est le parent du [membre](./member-object-ado-md.md) actuel dans une hiérarchie.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un objet [membre](./member-object-ado-md.md) et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Un membre qui se trouve au niveau supérieur d’une hiérarchie (la racine) n’a pas de parent. Cette propriété est prise en charge uniquement sur les objets **membres** appartenant à un objet de [niveau](./level-object-ado-md.md) . Une erreur se produit quand cette propriété est référencée à partir d’objets **membres** appartenant à un objet [position](./position-object-ado-md.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](./member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Children, propriété (ADO MD)](./children-property-ado-md.md)