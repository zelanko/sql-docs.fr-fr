---
title: FieldEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- FieldEnum
helpviewer_keywords:
- FieldEnum enumeration [ADO]
ms.assetid: be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b00bf49dc7ee74c6da15b078e674af5e0472ec6
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="fieldenum"></a>FieldEnum
Spécifie les champs spéciaux référencés dans un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) l’objet [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection.  
  
## <a name="remarks"></a>Notes  
 Ces constantes fournissent un « raccourci » pour accéder aux champs spéciaux associés une **enregistrement**. Récupérer le [champ](../../../ado/reference/ado-api/field-object.md) de l’objet à partir de la **champs** collection, puis obtenez son contenu avec le **champ** l’objet [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Fait référence au champ contenant la valeur par défaut [flux](../../../ado/reference/ado-api/stream-object-ado.md) objet associé à un **enregistrement**.|  
|**adRecordURL**|-2|Fait référence au champ contenant la chaîne URL absolue pour actuel **enregistrement**.|
