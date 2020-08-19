---
description: DrilledDown, propriété (ADO MD)
title: Propriété DrilledDown (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DrilledDown
- Member::DrilledDown
helpviewer_keywords:
- DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
author: rothja
ms.author: jroth
ms.openlocfilehash: 132b1a7210a9fd37866f1a150430f0d1a6d29606
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441041"
---
# <a name="drilleddown-property-ado-md"></a>DrilledDown, propriété (ADO MD)
Indique si les enfants suivent immédiatement le [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) sur l’axe.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne une valeur **booléenne** et est en lecture seule. **DrilledDown** retourne la **valeur true** s’il n’y a aucun membre enfant du membre actuel sur l’axe. **DrilledDown** retourne la **valeur false** si le membre actuel possède un ou plusieurs membres enfants sur l’axe.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **DrilledDown** pour déterminer s’il existe au moins un enfant de ce membre sur l’axe qui suit immédiatement ce membre. Ces informations sont utiles lors de l’affichage du membre.  
  
 Cette propriété est uniquement prise en charge sur les objets [membres](../../../ado/reference/ado-md-api/member-object-ado-md.md) appartenant à un objet [position](../../../ado/reference/ado-md-api/position-object-ado-md.md) . Une erreur se produit quand cette propriété est référencée à partir d’objets **membres** appartenant à un objet de [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ParentSameAsPrev, propriété (ADO MD)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
