---
title: compareTo, méthode (DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3f70413a7624b9bbd380a664fbf61b9a33f8989b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67955515"
---
# <a name="compareto-method-datetimeoffset"></a>Méthode compareTo (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Compare cet objet **DateTimeOffset** à un autre objet **DateTimeOffset** en fonction de l’heure à l’heure GMT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int compareTo(DateTimeOffset other)  
```  
  
#### <a name="parameters"></a>Paramètres  
 Valeur [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) à comparer à l’instance actuelle.  
  
## <a name="return-value"></a>Valeur retournée  
 Le tableau suivant décrit la valeur renvoyée par cette méthode :  
  
|Valeur retournée|Description|  
|------------------|-----------------|  
|0|Les deux objets **DateTimeOffset** représentent le même point dans le temps.|  
|nombre négatif|Cet objet **DateTimeOffset** représente un point dans le temps antérieur à *other*.|  
|nombre positif|Cet objet **DateTimeOffset** représente un point dans le temps qui est après *other*.|  
  
## <a name="remarks"></a>Notes  
 Lorsque deux objets **DateTimeOffset** ont la même heure GMT, ils ne sont pas triés en fonction du décalage.  
  
## <a name="see-also"></a>Voir aussi  
 [DateTimeOffset, classe](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
