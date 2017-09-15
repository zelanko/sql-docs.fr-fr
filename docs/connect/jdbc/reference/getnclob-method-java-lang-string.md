---
title: "Méthode getNClob (java.lang.String) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be01ce56-8f13-437b-8de6-246cda5f7830
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd11b3bc0f6a43ffcc504b99b117e3eab5170749
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getnclob-method-javalangstring"></a>Méthode getNClob (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur d’un JDBC **NCLOB** paramètre en tant qu’objet NClob dans le langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.NClob getNClob(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 A **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 ANClobobject.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getNClob est spécifiée par la méthode getNClob dans l’interface java.sql.CallableStatement.  
  
 Cette méthode prend uniquement en charge la récupération de **NCHAR**, **NVARCHAR**, **NTEXT**, et **XML** paramètres. L'appel de ces méthodes sur d'autres paramètres de type de données entraîne une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getNClob &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
