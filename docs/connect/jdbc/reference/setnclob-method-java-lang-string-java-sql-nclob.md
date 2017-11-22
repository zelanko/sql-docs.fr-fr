---
title: "Méthode setNClob (java.lang.String, java.sql.NClob) | Documents Microsoft"
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
ms.assetid: 4e30d242-0c1b-45db-b75f-41b041692f31
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0e920c0079bd431926a669ff2fd0033d2bc051dd
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setnclob-method-javalangstring-javasqlnclob"></a>Méthode setNClob (java.lang.String, java.sql.NClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné à l’objet NClob spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setNClob(java.lang.String parameterName,  
              java.sql.NClob value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 A **chaîne** qui contient le nom du paramètre.  
  
 *valeur*  
  
 Un objet NClob.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode doit être utilisée pour **NCHAR**, **NVARCHAR**, **NTEXT**, et **XML** les types de données de paramètre.  
  
 Cette méthode setNClob est spécifiée par la méthode setNClob dans l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setNClob &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
