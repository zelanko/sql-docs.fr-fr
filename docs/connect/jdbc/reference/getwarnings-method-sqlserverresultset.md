---
description: Méthode getWarnings (SQLServerResultSet)
title: Méthode getWarnings (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getWarnings
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb4339b0-383b-4337-a935-e8ec3f0d4123
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 74d18c8739a61b15fbbc7fb9606a211cae62f32b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433791"
---
# <a name="getwarnings-method-sqlserverresultset"></a>Méthode getWarnings (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le premier avertissement signalé par des appels sur cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
> [!NOTE]  
>  Actuellement, cette méthode n’est pas prise en charge par le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Si elle est appelée, cette méthode retourne toujours une valeur Null.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.SQLWarning getWarnings()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet SQLWarning.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getWarnings est spécifiée par la méthode getWarnings de l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
