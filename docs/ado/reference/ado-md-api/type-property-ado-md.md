---
description: Type, propriété (ADO MD)
title: Type, propriété (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member::Type
- Type
helpviewer_keywords:
- Type property [ADO MD]
ms.assetid: 34698910-64b9-41d8-8531-9de12f2b1e32
author: rothja
ms.author: jroth
ms.openlocfilehash: 52b07fe68f905c7f27bad4685d5df56c25cb2c13
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985970"
---
# <a name="type-property-ado-md"></a>Type, propriété (ADO MD)
Indique le type du [membre](./member-object-ado-md.md)actuel.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne une valeur [MemberTypeEnum](./membertypeenum.md) et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Cette propriété est prise en charge uniquement sur les objets [membres](./member-object-ado-md.md) appartenant à un objet de [niveau](./level-object-ado-md.md) . Une erreur se produit quand cette propriété est référencée à partir d’objets **membres** appartenant à un objet [position](./position-object-ado-md.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](./member-object-ado-md.md)