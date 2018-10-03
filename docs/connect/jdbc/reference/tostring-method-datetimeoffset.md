---
title: toString, méthode (DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 990cb7cccd972ac926824ca3f8d99de3f0d6e305
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687737"
---
# <a name="tostring-method-datetimeoffset"></a>Méthode toString (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une représentation de chaîne de la **DateTimeOffset** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Une chaîne représentant le **DateTimeOffset** objet.  
  
## <a name="remarks"></a>Notes   
 La chaîne a le format *aaaa*-*MM*-*jj ** hh*:*mm*:*ss*[. *fffffff*] [+ |-]*hh*:*mm*.  
  
 Les fractions de seconde de la chaîne renvoyée sont remplies avec des zéros jusqu'à la précision déclarée. Par exemple, un **datetimeoffset(6)** avec la valeur « 12:34:56.78 2010-03-10-08:00 » sera formaté en DateTimeOffset.toString en tant que « 12:34:56.780000 2010-03-10-08:00 ".  
  
## <a name="see-also"></a> Voir aussi  
 [DateTimeOffset, classe](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset, membres](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
