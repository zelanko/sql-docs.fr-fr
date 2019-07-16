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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5fe89d90510e95468e18b0d744ff566f69654320
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932683"
---
# <a name="fieldenum"></a>FieldEnum
Spécifie les champs spéciaux référencés dans un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) l’objet [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection.  
  
## <a name="remarks"></a>Notes  
 Ces constantes représentent un « raccourci » pour accéder aux champs spéciaux associés un **enregistrement**. Récupérer le [champ](../../../ado/reference/ado-api/field-object.md) de l’objet à partir de la **champs** collection, puis obtenez son contenu avec le **champ** l’objet [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Fait référence au champ qui contient la valeur par défaut [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet associé à un **enregistrement**.|  
|**adRecordURL**|-2|Fait référence au champ qui contient la chaîne d’URL absolue pour actuel **enregistrement**.|
