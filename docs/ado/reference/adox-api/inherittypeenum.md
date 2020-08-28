---
description: InheritTypeEnum
title: InheritTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 37c6eba57eb7efb05d2b718e294e33b9616cac77
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984100"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Spécifie la manière dont les objets héritent des autorisations définies avec [SetPermissions](./setpermissions-method-adox.md).  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Les objets et les autres conteneurs contenus dans l’objet principal héritent de l’entrée.|  
|**adInheritContainers**|2|Les autres conteneurs qui sont contenus par l’objet principal héritent de l’entrée.|  
|**adInheritNone**|0|Par défaut. Aucun héritage n’a lieu.|  
|**adInheritNoPropagate**|4|Les indicateurs **adInheritObjects** et **adInheritContainers** ne sont pas propagés à une entrée héritée.|  
|**adInheritObjects**|1|Les objets qui ne sont pas des conteneurs dans le conteneur héritent des autorisations.|  
  
## <a name="applies-to"></a>S'applique à  
 [SetPermissions, méthode (ADOX)](./setpermissions-method-adox.md)