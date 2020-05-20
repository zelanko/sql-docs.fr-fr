---
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
ms.openlocfilehash: 24d69ac1406363458c8dbd3168e6d25309cfa2c4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762570"
---
# <a name="fieldenum"></a>FieldEnum
Spécifie les champs spéciaux référencés dans la collection de [champs](../../../ado/reference/ado-api/fields-collection-ado.md) d’un objet [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) .  
  
## <a name="remarks"></a>Notes  
 Ces constantes fournissent un « raccourci » pour accéder à des champs spéciaux associés à un **enregistrement**. Récupérez l’objet de [champ](../../../ado/reference/ado-api/field-object.md) à partir de la collection de **champs** , puis obtenez son contenu avec la propriété [value](../../../ado/reference/ado-api/value-property-ado.md) de l’objet **Field** .  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Fait référence au champ contenant l’objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) par défaut associé à un **enregistrement**.|  
|**adRecordURL**|-2|Fait référence au champ contenant la chaîne d’URL absolue pour l' **enregistrement**en cours.|
