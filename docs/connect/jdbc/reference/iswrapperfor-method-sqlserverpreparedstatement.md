---
title: Méthode isWrapperFor (SQLServerPreparedStatement) | Documents Microsoft
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
ms.assetid: b0e591b1-73e2-4f90-967f-5555eadfc3f1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3920e10bb7fc100879b1ab52e19e2ef9705cf5b6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="iswrapperfor-method-sqlserverpreparedstatement"></a>Méthode isWrapperFor (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si cet objet d'instruction est un wrapper pour l'interface spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *iface*  
  
 A **classe** définissant une interface.  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si cet objet implémente l’interface ou encapsule un objet qui implémente l’interface. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 La méthode [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md) et la méthode [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md) sont définies par l’interface java.sql.Wrapper, introduite dans les spécifications de JDBC 4.0.  
  
 Si cette méthode retourne la valeur True, l’appel de [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md) avec le même argument réussit.  
  
 Pour plus d’informations, consultez [Wrappers et Interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [unwrap, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
