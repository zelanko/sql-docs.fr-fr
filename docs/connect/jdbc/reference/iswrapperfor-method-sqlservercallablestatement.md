---
title: Méthode isWrapperFor (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 71156863-3588-453e-b5a5-0573b2c1bebf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5b1a572d3ab2dfba9d0aa0b8284fc770f3422782
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977099"
---
# <a name="iswrapperfor-method-sqlservercallablestatement"></a>Méthode isWrapperFor (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si cet objet d'instruction est un wrapper pour l'interface spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *iface*  
  
 **Classe** définissant une interface.  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si cet objet implémente l’interface ou encapsule un objet qui implémente l’interface. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Les méthodes [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md) et [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md) sont définies par l’interface java.sql.Wrapper, introduite dans JDBC 4.0.  
  
 Si cette méthode retourne **true**, l’appel de [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md) avec le même argument réussit.  
  
 Pour plus d’informations, consultez [wrappers et interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [unwrap, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
