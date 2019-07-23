---
title: Méthode getMinutesOffset (DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 18ba844a-ea36-42de-87da-bbc222082efe
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6af552920698d4eb149f5edd5ee50128db0e1b61
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981799"
---
# <a name="getminutesoffset-method-datetimeoffset"></a>Méthode getMinutesOffset (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le décalage, en minutes par rapport à l’heure GMT, de cet objet DateTimeOffset.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getMinutesOffset()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Décalage en minutes.  
  
## <a name="remarks"></a>Notes  
 Pour un objet DateTimeOffset représentant 8 mars 2010, 11:35:48 -0800, getMinutesOffset retourne la valeur 480.  
  
## <a name="see-also"></a>Voir aussi  
 [DateTimeOffset, classe](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
