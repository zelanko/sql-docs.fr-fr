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
ms.topic: conceptual
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b8d13a403cff4d6b3f955bf560ef17f98eae36d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
  
  
