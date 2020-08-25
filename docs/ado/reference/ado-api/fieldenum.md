---
description: FieldEnum
title: FieldEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldEnum
helpviewer_keywords:
- FieldEnum enumeration [ADO]
ms.assetid: be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2
author: rothja
ms.author: jroth
ms.openlocfilehash: cad540a13fbad480f795049df0d0150188df4283
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775448"
---
# <a name="fieldenum"></a>FieldEnum
Spécifie les champs spéciaux référencés dans la collection de [champs](./fields-collection-ado.md) d’un objet [enregistrement](./record-object-ado.md) .  
  
## <a name="remarks"></a>Notes  
 Ces constantes fournissent un « raccourci » pour accéder à des champs spéciaux associés à un **enregistrement**. Récupérez l’objet de [champ](./field-object.md) à partir de la collection de **champs** , puis obtenez son contenu avec la propriété [value](./value-property-ado.md) de l’objet **Field** .  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Fait référence au champ contenant l’objet de [flux](./stream-object-ado.md) par défaut associé à un **enregistrement**.|  
|**adRecordURL**|-2|Fait référence au champ contenant la chaîne d’URL absolue pour l' **enregistrement**en cours.|