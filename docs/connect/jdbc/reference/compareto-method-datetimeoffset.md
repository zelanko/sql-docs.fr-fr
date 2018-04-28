---
title: Méthode compareTo (DateTimeOffset) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b8307787576f520f83ceeffe10c830cd06a16d69
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="compareto-method-datetimeoffset"></a>Méthode compareTo (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Compare cette **DateTimeOffset** objet vers un autre **DateTimeOffset** objet basé sur l’heure à l’heure GMT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int compareTo(DateTimeOffset other)  
```  
  
#### <a name="parameters"></a>Paramètres  
 A [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valeur que vous souhaitez comparer à l’instance actuelle.  
  
## <a name="return-value"></a>Valeur retournée  
 Le tableau suivant décrit la valeur renvoyée par cette méthode :  
  
|Valeur retournée| Description|  
|------------------|-----------------|  
|0|Les deux **DateTimeOffset** objets représentent le même point dans le temps.|  
|nombre négatif|Cela **DateTimeOffset** objet représente un point dans le temps qui précède *autres*.|  
|nombre positif|Cela **DateTimeOffset** objet représente un point dans le temps qui se trouve après *autres*.|  
  
## <a name="remarks"></a>Notes  
 Lorsque deux **DateTimeOffset** objets ont la même heure à l’heure GMT, il n’existe aucun autre classement des objets en fonction de l’offset.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
