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
ms.openlocfilehash: 87c61baa93cb1dbca58bbe86ffc254a92d2b9d5b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67965243"
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
