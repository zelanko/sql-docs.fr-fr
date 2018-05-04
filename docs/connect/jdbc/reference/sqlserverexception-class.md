---
title: Classe SQLServerException | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 56766dec21b0e823174eeccbaf16a02de2b5578a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
  
  
