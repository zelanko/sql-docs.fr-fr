---
title: "Méthode getLong (int) | Documents Microsoft"
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
apiname: SQLServerCallableStatement.getLong (int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: b7078ca7-fd2a-4474-ab29-989ae28c77e8
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6ea3222ca2f4dd4b1e1a18005e3397caad736190
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getlong-method-int"></a>Méthode getLong (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant qu’un **long** en fonction de l’index de paramètre de langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public long getLong(int index)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 A **long** valeur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getLong est spécifiée par la méthode getLong dans l’interface java.sql.CallableStatement.  
  
 Cette méthode est prise en charge uniquement sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] des types de données qui peuvent retourner en toute sécurité une valeur entière, tels que bigint, int, smallint, tinyint et bit. L'utilisation de cette méthode sur n'importe quel autre type de données entraîne la levée d'une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getLong &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getlong-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
