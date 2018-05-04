---
title: Méthode setBoolean (SQLServerCallableStatement) | Documents Microsoft
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
- SQLServerCallableStatement.setBoolean
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8cd810b1-9858-4e51-9535-239d864cd288
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9b4c8d83a24fa479e1a93c08f8b96a5ee619f6e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="setboolean-method-sqlservercallablestatement"></a>Méthode setBoolean (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon la donnée **booléenne** valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setBoolean(java.lang.String sCol,  
                       boolean b)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 A **chaîne** qui contient le nom du paramètre.  
  
 *B*  
  
 A **booléenne** valeur, soit **true** ou **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setBoolean est spécifiée par la méthode setBoolean dans l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
