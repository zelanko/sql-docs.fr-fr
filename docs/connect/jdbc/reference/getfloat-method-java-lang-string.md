---
title: "Méthode getFloat (java.lang.String) | Documents Microsoft"
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
apiname: SQLServerCallableStatement.getFloat (java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: b6492341-fdc2-449c-9d03-95a5dadf1bb0
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 208bba07d833dbdbb80bd88d8e9cd5aeee1a2a46
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getfloat-method-javalangstring"></a>Méthode getFloat (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant qu’un **float** en fonction du nom du paramètre de langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public float getFloat(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 A **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 A **float** valeur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getFloat est spécifiée par la méthode getFloat dans l’interface java.sql.CallableStatement.  
  
 Cette méthode retourne tous les types de nombres avec Java **float** fidélité.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getFloat &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getfloat-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
