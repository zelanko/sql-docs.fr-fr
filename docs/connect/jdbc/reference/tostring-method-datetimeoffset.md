---
title: "Méthode toString (DateTimeOffset) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c6dd16bfddfa331fd2647bd8fd191ac91941e71
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="tostring-method-datetimeoffset"></a>Méthode toString (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une représentation de chaîne de la **DateTimeOffset** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Représentation de chaîne de la **DateTimeOffset** objet.  
  
## <a name="remarks"></a>Notes  
 La chaîne a le format *aaaa*-*MM*-*jj**hh*:*mm*: *ss*[. *fffffff*] [+ |-]*hh*:*mm*.  
  
 Les fractions de seconde de la chaîne renvoyée sont remplies avec des zéros jusqu'à la précision déclarée. Par exemple, un **datetimeoffset(6)** avec la valeur « 2010-03-10 12:34:56.78 -08:00 » sera formaté en DateTimeOffset.toString en tant que « 2010-03-10 12:34:56.780000 -08:00 ".  
  
## <a name="see-also"></a>Voir aussi  
 [Classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
