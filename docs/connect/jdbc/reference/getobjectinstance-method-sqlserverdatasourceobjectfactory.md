---
title: Méthode getObjectInstance (SQLServerDataSourceObjectFactory) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSourceObjectFactory.getObjectInstance
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0a1503e2-e991-4d70-a223-087fc63baf73
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 13da5aeb7015255f0ff4b7a540b62462439ce30d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66765669"
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
  
 Valeur **Object**.  
  
 *nom*  
  
 Nom de l'objet.  
  
 *c*  
  
 Contexte relatif au nom spécifié.  
  
 *h*  
  
 Environnement qui est utilisé dans la création de l'objet.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur **Object**.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode getObjectInstance est spécifiée par la méthode getObjectInstance dans l’interface javax.naming.spi.ObjectFactory.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSourceObjectFactory, méthodes](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-methods.md)   
 [SQLServerDataSourceObjectFactory, membres](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [SQLServerDataSourceObjectFactory, classe](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)  
  
  
