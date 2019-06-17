---
title: Classe SQLServerConnection | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 937292a6-1525-423e-a2b2-a18fd34c2893
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a14627f54e1d297642cb2c555fb8427acb2da5a7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803091"
---
# <a name="sqlserverconnection-class"></a>Classe SQLServerConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente une connexion JDBC à une base de données [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Implémente :** [ISQLServerConnection](../../../connect/jdbc/reference/isqlserverconnection-interface.md), java.io.Serializable  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerConnection  
```  
  
## <a name="remarks"></a>Notes  
 SQLServerConnection prend en charge la mise en pool de connexions JDBC sous la forme d’une connexion JDBC physique ou logique. SQLServerConnection gère le contrôle des transactions pour toutes les instructions qu’il crée et peut participer aux transactions XA distribuées gérées via un adaptateur XAResource.  
  
 SQLServerConnection gère un pool de descripteurs d’instruction préparée. Les instructions préparées le sont une seule fois et sont généralement exécutées plusieurs fois avec des valeurs de données différentes pour leurs paramètres. Les instructions préparées sont également conservées entre deux fermetures d'une connexion logique (regroupée).  
  
> [!NOTE]  
>  SQLServerConnection n’est pas thread-safe. Toutefois, il est possible de traiter simultanément dans des threads simultanés plusieurs instructions créées à partir d'une seule connexion.  
  
 Cette classe prend en charge la Désencapsulation dans la classe SQLServerConnection, interface java.sql.connection et interface ISQLServerConnection. Pour plus d’informations, consultez [Wrappers et Interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
