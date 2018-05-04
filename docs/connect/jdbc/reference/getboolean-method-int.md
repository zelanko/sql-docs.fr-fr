---
title: Méthode getBoolean (int) | Documents Microsoft
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
apiname:
- SQLServerCallableStatement.getBoolean (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4d9db847-df22-40ab-8a5c-ec9158c576ca
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f4b6c9d23c1d43336a6b83bd634c075705c8c507
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="getboolean-method-int"></a>Méthode getBoolean (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant qu’un **booléenne** valeur en fonction de l’index de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getBoolean(int index)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 A **booléenne** valeur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getBoolean est spécifiée par la méthode getBoolean dans l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getBoolean &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getboolean-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
