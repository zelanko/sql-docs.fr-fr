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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965243"
---
# <a name="ruleenum"></a>RuleEnum
Spécifie la règle à suivre lorsqu’une [clé](../../../ado/reference/adox-api/key-object-adox.md) est supprimée.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adRICascade**|1|Modifications en cascade.|  
|**adRINone**|0|valeur par défaut. Aucune action n'est effectuée.|  
|**adRISetDefault**|3|La valeur de clé étrangère est définie sur la valeur par défaut.|  
|**adRISetNull**|2|La valeur de clé étrangère est définie sur null.|  
  
## <a name="applies-to"></a>S'applique à  
 [DeleteRule, propriété (ADOX)](../../../ado/reference/adox-api/deleterule-property-adox.md)
