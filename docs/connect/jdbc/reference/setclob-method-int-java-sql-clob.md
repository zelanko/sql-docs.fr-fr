---
title: Méthode setClob (int, java.sql.Clob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setClob
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 68d49f2c-fd8d-4abb-bfdc-e7b0fbd9a9da
author: MightyPen
ms.author: genemi
ms.openlocfilehash: abbd62ffbd256334511a30ae89091618ec37abf9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67974566"
---
# <a name="setclob-method-int-javasqlclob"></a>Méthode setClob (int, java.sql.Clob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet Clob donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setClob(int parameterIndex,  
                          java.sql.Clob clobValue)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 **int** indiquant le numéro du paramètre.  
  
 *clobValue*  
  
 Objet Clob.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setClob est spécifiée par la méthode setClob de l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerPreparedStatement, méthodes](../../../connect/jdbc/reference/sqlserverpreparedstatement-methods.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
