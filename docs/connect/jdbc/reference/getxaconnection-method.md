---
title: Méthode getXAConnection () | Documents Microsoft
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
- SQLServerXADataSource.getXAConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2710613-78b1-438f-b996-c7ae6f34381a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1428be2a569818d85447718042d7cf33cab66600
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="getxaconnection-method-"></a>Méthode getXAConnection ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Essaie d'établir une connexion de base de données physique qui peut être utilisée dans une transaction distribuée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public javax.sql.XAConnection getXAConnection()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet XAConnection.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode getXAConnection est spécifiée par la méthode getXAConnection dans l’interface javax.sql.XADataSource.  
  
> [!NOTE]  
>  Cette méthode est généralement appelée par les implémentations de regroupement de connexions XA et non par le code d'application JDBC normal.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getXAConnection &#40;SQLServerXADataSource&#41;](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)   
 [Méthodes SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [Membres de SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [SQLServerXADataSource, classe](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
