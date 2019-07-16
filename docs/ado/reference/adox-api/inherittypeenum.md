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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67965953"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Spécifie comment les objets héritent des autorisations définies avec [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md).  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Objets et autres conteneurs de l’objet principal héritent de l’entrée.|  
|**adInheritContainers**|2|Autres conteneurs qui sont contenus par l’objet principal héritent de l’entrée.|  
|**adInheritNone**|0|Valeur par défaut. Aucun héritage se produit.|  
|**adInheritNoPropagate**|4|Le **indicateurs adInheritObjects** et **adInheritContainers ne** indicateurs ne sont pas propagées à une entrée héritée.|  
|**adInheritObjects**|1|Objets non-container dans le conteneur héritent des autorisations.|  
  
## <a name="applies-to"></a>S'applique à  
 [SetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
