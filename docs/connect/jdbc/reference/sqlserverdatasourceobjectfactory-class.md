---
title: Classe SQLServerDataSourceObjectFactory | Documents Microsoft
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
ms.topic: article
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7900f5018dfe5af2643419e91320b2ff02cce615
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverdatasourceobjectfactory-class"></a>Classe SQLServerDataSourceObjectFactory
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente une fabrique d'objet permettant de matérialiser des sources de données à partir de JNDI (Java Naming and Directory Interface).  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.lang.Object  
  
 **Implémente :** javax.naming.spi.ObjectFactory  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>Notes  
 Cette méthode est héritée par toutes les classes de source de données. Dans le cadre de sa prise en charge de l’interface Referenceable, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] expose cette classe qui implémente un ObjectFactory. Serveurs d’applications Java appellera getReference sur une classe de source de données, et cela crée un objet de référence qui utilise en interne le nom de classe en tant que fabrique de classe.  
  
 Lorsque le serveur d’applications Java doit déréférencer l’objet de référence, elle crée une instance de l’objet de SQLServerDataSourceObjectFactory et appelle le [getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md) méthode, en passant à l’objet de référence récupérer l’instance de source de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Référence d’API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
