---
title: "Méthode getDateTimeOffset (int) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bb00356-4d6e-4625-b924-67646930fdf2
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3171789255d0184715917429c7627aadd734d62e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getdatetimeoffset-method-int"></a>Méthode getDateTimeOffset (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Cette méthode a été ajoutée dans [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] version 3.0 du pilote JDBC.  
  
 Récupère la valeur du paramètre désigné en tant qu’un [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) objet en fonction de l’index de paramètre de langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(int index)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 Position ordinale du paramètre de base un.  
  
## <a name="return-value"></a>Valeur retournée  
 A [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) objet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Vous pouvez définir un [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valeur de paramètre avec [SQLServerCallableStatement.setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getDateTimeOffset &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

