---
title: RuleEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RuleEnum
helpviewer_keywords:
- RuleEnum enumeration [ADOX]
ms.assetid: 738fd3ff-3daf-483d-a0b9-88bef1be54c1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 77d488bd128f4f5cfa905586f2130cd90be6354c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705841"
---
# <a name="ruleenum"></a>RuleEnum
Spécifie la règle à appliquer quand une [clé](../../../ado/reference/adox-api/key-object-adox.md) est supprimé.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adRICascade**|1|Modifications en cascade.|  
|**adRINone**|0|Valeur par défaut. Aucune action n'est effectuée.|  
|**adRISetDefault**|3|Valeur de clé étrangère est définie à la valeur par défaut.|  
|**adRISetNull**|2|Valeur de clé étrangère est définie sur null.|  
  
## <a name="applies-to"></a>S'applique à  
 [DeleteRule, propriété (ADOX)](../../../ado/reference/adox-api/deleterule-property-adox.md)
