---
title: "Méthode Unwrap (SQLServerConnectionPoolDataSource) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5c9b734-2096-4ae4-a284-6b4d1b4a00d4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8e19a9c15e6bced2f9b0df99e491cdbb0ac8240a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="unwrap-method-sqlserverconnectionpooldatasource"></a>Méthode unwrap (SQLServerConnectionPoolDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne un objet qui implémente l’interface spécifiée pour autoriser l’accès à la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-des méthodes spécifiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *iface*  
  
 Une classe de type **T** définissant une interface.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet qui implémente l'interface spécifiée.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Le [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md) méthode est définie par l’interface java.sql.Wrapper, introduite dans les spécifications de JDBC 4.0.  
  
 Les applications devront peut-être accéder à des extensions de l’API JDBC qui sont spécifiques à la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. La méthode unwrap prend en charge la Désencapsulation dans les classes publiques par cet objet, si les classes exposent des extensions de fournisseur.  
  
 Le [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) classe étend la [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) classe. Lorsque cette méthode est appelée, l’objet se désencapsule dans les [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) classe et le [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) classe.  
  
 Pour plus d’informations, consultez [Wrappers et Interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-methods.md)   
 [Membres de SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [SQLServerConnectionPoolDataSource, classe](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  

