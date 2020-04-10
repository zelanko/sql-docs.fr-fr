---
title: Méthode compareTo (DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ac80b43813106f1de991da5114b2473871222a68
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923580"
---
# <a name="compareto-method-datetimeoffset"></a>Méthode compareTo (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Compare cet objet **DateTimeOffset** à un autre objet **DateTimeOffset** en fonction de l’heure GMT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int compareTo(DateTimeOffset other)  
```  
  
#### <a name="parameters"></a>Paramètres  
 Valeur [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) à comparer à l’instance actuelle.  
  
## <a name="return-value"></a>Valeur de retour  
 Le tableau suivant décrit la valeur renvoyée par cette méthode :  
  
|Valeur retournée|Description|  
|------------------|-----------------|  
|0|Les deux objets **DateTimeOffset** représente le même point dans le temps.|  
|nombre négatif|Cet objet **DateTimeOffset** représente un point dans le temps antérieur à *other*.|  
|nombre positif|Cet objet **DateTimeOffset** représente un point dans le temps postérieur à *other*.|  
  
## <a name="remarks"></a>Notes  
 Lorsque deux objets **DateTimeOffset** ont la même heure GMT, ils ne sont pas triés en fonction du décalage.  
  
## <a name="see-also"></a>Voir aussi  
 [DateTimeOffset, classe](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
