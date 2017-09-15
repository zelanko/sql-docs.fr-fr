---
title: Classe SQLServerException | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd894bf23d8b1643722691451ccf3ae29ec6cd54
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverexception-class"></a>Classe SQLServerException
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente une exécution incorrecte ou incomplète d'une instruction SQL.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.sql.SQLException  
  
 **Implémente :** java.io.Serializable  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final class SQLServerException  
```  
  
## <a name="remarks"></a>Notes  
 La classe SQLServerException gère les codes d’état SQL 92 et XOPEN. Il est possible de passer de l'un à l'autre à l'aide d'une propriété de connexion spécifiée par l'utilisateur. Les exceptions sont écrites dans les fichiers journaux ouverts qui ont été spécifiés.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Référence d’API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
