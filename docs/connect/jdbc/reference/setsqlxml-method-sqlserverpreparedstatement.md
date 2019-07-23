---
title: setSQLXML, méthode (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 70bbdde0-75f7-4169-88c5-dbbe2c4bcd03
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b2a1af43238d2f0da19c65535f3c6f84fa0e434f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972802"
---
# <a name="setsqlxml-method-sqlserverpreparedstatement"></a>Méthode setSQLXML (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet SQLXML spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setSQLXML(int parameterIndex,  
                            java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 **Entier** qui indique l’index du paramètre.  
  
 *xmlObject*  
  
 Objet SQLXML contenant la valeur du paramètre.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setSQLXML est spécifiée par la méthode setSQLXML de l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
