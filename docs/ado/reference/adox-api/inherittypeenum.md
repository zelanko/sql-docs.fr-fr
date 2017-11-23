---
title: InheritTypeEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: InheritTypeEnum
helpviewer_keywords: InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9269c58d9f5c172a6c640668382b00fd66c5dda0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Indique comment les objets hériteront des autorisations définies dans [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md).  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Les objets et les autres conteneurs contenus dans l’objet principal héritent de l’entrée.|  
|**adInheritContainers ne**|2|Autres conteneurs qui sont contenus dans l’objet principal héritent de l’entrée.|  
|**adInheritNone**|0|Valeur par défaut. Aucun héritage se produit.|  
|**adInheritNoPropagate**|4|Le **indicateurs adInheritObjects** et **adInheritContainers ne** indicateurs ne sont pas propagées à une entrée héritée.|  
|**indicateurs adInheritObjects**|1|Les objets autres que des conteneurs dans le conteneur héritent des autorisations.|  
  
## <a name="applies-to"></a>S'applique à  
 [SetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
