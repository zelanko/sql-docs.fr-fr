---
title: Méthode getObjectInstance (SQLServerDataSourceObjectFactory) | Documents Microsoft
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
apiname:
- SQLServerDataSourceObjectFactory.getObjectInstance
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0a1503e2-e991-4d70-a223-087fc63baf73
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 38ed185d36188d4889ee35e9188aa907324c9038
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getobjectinstance-method-sqlserverdatasourceobjectfactory"></a>Méthode getObjectInstance (SQLServerDataSourceObjectFactory)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une instance de l'objet source de données spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.Object getObjectInstance(java.lang.Object ref,  
                                          javax.naming.Name name,  
                                          javax.naming.Context c,  
                                          java.util.Hashtable h)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ref*  
  
 Un **objet** valeur.  
  
 *nom*  
  
 Nom de l'objet.  
  
 *c*  
  
 Contexte relatif au nom spécifié.  
  
 *H*  
  
 Environnement qui est utilisé dans la création de l'objet.  
  
## <a name="return-value"></a>Valeur retournée  
 Un **objet** valeur.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode getObjectInstance est spécifiée par la méthode getObjectInstance dans l’interface javax.naming.spi.ObjectFactory.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-methods.md)   
 [Membres de SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [SQLServerDataSourceObjectFactory, classe](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)  
  
  
