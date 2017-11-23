---
title: "Méthode getTimestamp (int, java.util.Calendar) | Documents Microsoft"
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
apiname: SQLServerCallableStatement.getTimestamp (int, java.util.Calendar)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 161c559a-8651-44ba-a914-15eb6a612417
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ce7ad759d6901ccdc641d693f836180a1152fe84
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="gettimestamp-method-int-javautilcalendar"></a>Méthode getTimestamp (int, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant qu’objet java.sql.Timestamp dans le langage de programmation donné de l’index de paramètre, à l’aide d’un objet de calendrier de Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Timestamp getTimestamp(int index,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 Un **int** qui indique l’index de paramètre.  
  
 *licences d’accès client*  
  
 Un objet de calendrier.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet Timestamp.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTimestamp est spécifiée par la méthode getTimestamp dans l’interface java.sql.CallableStatement.  
  
 Cette méthode retourne des valeurs uniquement à partir de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** et **smalldatetime** colonnes.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getTimestamp &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
