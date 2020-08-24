---
description: MemberTypeEnum
title: MemberTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 186ef16dfaafac2151436a3cd63e944de2468457
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777958"
---
# <a name="membertypeenum"></a>MemberTypeEnum
Spécifie le paramètre pour la propriété [type](./type-property-ado-md.md) d’un objet [member](./member-object-ado-md.md) .  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adMemberAll**|4|Indique que l’objet **membre** représente tous les membres du niveau.|  
|**adMemberFormula**|3|Indique que l’objet **membre** est calculé à l’aide d’une expression de formule.|  
|**adMemberMeasure**|2|Indique que l’objet **membre** appartient à la dimension de mesures et représente un attribut quantitatif.|  
|**adMemberRegular**|1|Par défaut. Indique que l’objet **membre** représente une instance d’une entité métier.|  
|**adMemberUnknown**|0|Impossible de déterminer le type du membre.|