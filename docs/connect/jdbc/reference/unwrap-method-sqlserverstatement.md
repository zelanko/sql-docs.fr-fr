---
title: Unwrap, méthode (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce680176-ef04-4e44-bb6c-ec50bd06e7e6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a6823a9f6f57e1ebf1348f35d4a1478100962bb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47785546"
---
# <a name="unwrap-method-sqlserverstatement"></a>Méthode unwrap (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne un objet qui implémente l’interface spécifiée, afin d’autoriser l’accès aux méthodes propres au [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *iface*  
  
 Classe de type **T** définissant une interface.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet qui implémente l'interface spécifiée.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 La méthode [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) est définie par l’interface java.sql.Wrapper, introduite dans les spécifications de JDBC 4.0.  
  
 Les applications devront peut-être accéder à des extensions de l’API JDBC propres au [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. La méthode unwrap prend en charge la désencapsulation dans les classes publiques étendues par cet objet, si les classes exposent des extensions de fournisseur.  
  
 Lorsque cette méthode est appelée, l’objet se désencapsule dans la classe [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
 Par exemple de code, consultez [la mise à jour des exemples de données volumineux](../../../connect/jdbc/updating-large-data-sample.md), ou [unwrap, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md).  
  
 Pour plus d’informations, consultez [Wrappers et Interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a> Voir aussi  
 [isWrapperFor, méthode &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)   
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
