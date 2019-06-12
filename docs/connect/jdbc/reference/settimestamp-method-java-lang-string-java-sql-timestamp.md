---
title: setTimestamp, méthode à la valeur d’horodatage | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setTimestamp (java.lang.String, java.sql.Timestamp)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc45b126-3196-47ff-956b-cbc897980ff8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8edb9eec2f18fc133ccb64d9b43522a06ddad25b
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782716"
---
# <a name="settimestamp-method-javalangstring-javasqltimestamp"></a>Méthode setTimestamp (java.lang.String, java.sql.Timestamp)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon la valeur d'horodateur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setTimestamp(java.lang.String sCol,  
                         java.sql.Timestamp t)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *t*  
  
 Objet Timestamp.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setTimestamp est spécifiée par la méthode setTimestamp de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [setTimestamp, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/settimestamp-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
