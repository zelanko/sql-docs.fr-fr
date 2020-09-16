---
description: Méthode isWrapperFor (SQLServerPreparedStatement)
title: isWrapperFor, méthode (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b0e591b1-73e2-4f90-967f-5555eadfc3f1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 41f1855d202212d03561171a28e22d321d7547b0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433311"
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
  
 **Classe** définissant une interface.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si cet objet implémente l’interface ou encapsule un objet qui l’implémente. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 La méthode [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md) et la méthode [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md) sont définies par l’interface java.sql.Wrapper, introduite dans les spécifications de JDBC 4.0.  
  
 Si cette méthode retourne la valeur True, l’appel de [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md) avec le même argument réussit.  
  
 Pour plus d’informations, consultez [Wrappers et interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 [unwrap, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
