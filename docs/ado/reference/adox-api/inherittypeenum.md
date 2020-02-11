---
title: InheritTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- InheritTypeEnum
helpviewer_keywords:
- InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aef8f768dd991e4e6ed740cc56600a6f1a8020e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965953"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Spécifie la manière dont les objets héritent des autorisations définies avec [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md).  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Les objets et les autres conteneurs contenus dans l’objet principal héritent de l’entrée.|  
|**adInheritContainers**|2|Les autres conteneurs qui sont contenus par l’objet principal héritent de l’entrée.|  
|**adInheritNone**|0|valeur par défaut. Aucun héritage n’a lieu.|  
|**adInheritNoPropagate**|4|Les indicateurs **adInheritObjects** et **adInheritContainers** ne sont pas propagés à une entrée héritée.|  
|**adInheritObjects**|1|Les objets qui ne sont pas des conteneurs dans le conteneur héritent des autorisations.|  
  
## <a name="applies-to"></a>S'applique à  
 [SetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
