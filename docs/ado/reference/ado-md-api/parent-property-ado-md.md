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
ms.openlocfilehash: 4c599bd75388dc0b2ea7e4a5c16f495817f917ba
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440791"
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
