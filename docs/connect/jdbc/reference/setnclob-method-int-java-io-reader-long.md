---
title: "Méthode setNClob (int, java.io.Reader, long) | Documents Microsoft"
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
ms.assetid: 11071f8f-0e9b-45f0-b600-aaef7e2815d8
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f431dd89d52147080454bbedf5c081efdfa6997f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setnclob-method-int-javaioreader-long"></a>Méthode setNClob (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné à l’objet Reader spécifié, qui est le nombre de caractères spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setNClob(int parameterIndex,  
                    java.io.Reader reader,  
                    long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 Un **int** qui indique l’index de paramètre.  
  
 *lecteur*  
  
 Un objet de lecteur qui indique la valeur du paramètre.  
  
 *length*  
  
 Un **long** qui indique le nombre de caractères dans la valeur du paramètre.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setNClob est spécifiée par la méthode setNClob dans l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setNClob &#40; SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
