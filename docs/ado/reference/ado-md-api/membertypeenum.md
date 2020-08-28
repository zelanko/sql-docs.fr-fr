---
description: MemberTypeEnum
title: MemberTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- MemberTypeEnum
helpviewer_keywords:
- MemberTypeEnum enumeration [ADO MD]
ms.assetid: 5d8132c0-7ca2-4f86-8336-1b34213869ad
author: rothja
ms.author: jroth
ms.openlocfilehash: 441430cd164be017779afc54ba9af866edaea874
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986260"
---
# <a name="membertypeenum"></a>MemberTypeEnum
Spécifie le paramètre pour la propriété [type](./type-property-ado-md.md) d’un objet [member](./member-object-ado-md.md) .  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adMemberAll**|4|Indique que l’objet **membre** représente tous les membres du niveau.|  
|**adMemberFormula**|3|Indique que l’objet **membre** est calculé à l’aide d’une expression de formule.|  
|**adMemberMeasure**|2|Indique que l’objet **membre** appartient à la dimension de mesures et représente un attribut quantitatif.|  
|**adMemberRegular**|1|Par défaut. Indique que l’objet **membre** représente une instance d’une entité métier.|  
|**adMemberUnknown**|0|Impossible de déterminer le type du membre.|