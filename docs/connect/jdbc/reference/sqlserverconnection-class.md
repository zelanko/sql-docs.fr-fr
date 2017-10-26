---
title: Classe SQLServerConnection | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 937292a6-1525-423e-a2b2-a18fd34c2893
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a3beda0e5629888804b522e5c4e3123e0b959ba8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverconnection-class"></a>Classe SQLServerConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente une connexion JDBC à une [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] base de données.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Implémente :** [ISQLServerConnection](../../../connect/jdbc/reference/isqlserverconnection-interface.md), java.io.Serializable  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerConnection  
```  
  
## <a name="remarks"></a>Notes  
 SQLServerConnection prend en charge le regroupement de connexions JDBC et peut être une connexion JDBC physique ou une connexion JDBC logique. SQLServerConnection gère le contrôle de transaction pour toutes les instructions qui ont été créés à partir de celui-ci, et elle peut participer à des transactions distribuées XA gérées via un adaptateur XAResource.  
  
 SQLServerConnection gère un pool de descripteurs d’instruction préparée. Les instructions préparées le sont une seule fois et sont généralement exécutées plusieurs fois avec des valeurs de données différentes pour leurs paramètres. Les instructions préparées sont également conservées entre deux fermetures d'une connexion logique (regroupée).  
  
> [!NOTE]  
>  SQLServerConnection n’est pas thread-safe. Toutefois, il est possible de traiter simultanément dans des threads simultanés plusieurs instructions créées à partir d'une seule connexion.  
  
 Cette classe prend en charge la Désencapsulation dans la classe SQLServerConnection, interface java.sql.connection et interface ISQLServerConnection. Pour plus d’informations, consultez [Wrappers et Interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Référence d’API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

