---
title: Classe SQLServerPreparedStatement | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8481c06-fbba-432b-8c69-4f4619c20ad4
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cdcdd9e60abf105e1dc99c129e88837cb83d979a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverpreparedstatement-class"></a>Classe SQLServerPreparedStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente l'implémentation de base de la fonctionnalité d'instruction préparée JDBC.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** SQLServerStatement  
  
 **Implémente :** [ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerPreparedStatement  
```  
  
## <a name="remarks"></a>Notes  
 SQLServerPreparedStatement fournit des méthodes qui vous permettent de fournir des paramètres comme n’importe quel type Java natif et de nombreux types d’objets Java. SQLServerPreparedStatement prépare une instruction à l’aide de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **sp_prepare** procédure stockée, puis réutilise le retourné handle d’instruction pour chaque suivantes en cours d’exécution de l’instruction, généralement à l’aide de différents paramètres fournis par l’utilisateur.  
  
 SQLServerPreparedStatement prend en charge le traitement par lot, où un ensemble d’instructions préparées sont exécutées dans une base de données complet, pour améliorer les performances d’exécution.  
  
 Cette classe prend en charge la Désencapsulation dans la classe SQLServerPreparedStatement, interface ISQLServerPreparedStatement, interface java.sql.PreparedStatement et les classes et interfaces prises en charge par SQLServerStatement pour la Désencapsulation. Pour plus d’informations, consultez [Wrappers et Interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Référence d’API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
