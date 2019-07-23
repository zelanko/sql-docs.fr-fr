---
title: setUnicodeStream, méthode (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setUnicodeStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0a413e83-e0a4-41f8-9fe0-33ce4d368ee4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a80dddc28fbca156fe31a7620f1d1b0460359a75
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972158"
---
# <a name="setunicodestream-method-sqlserverpreparedstatement"></a>setUnicodeStream, méthode (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le numéro de paramètre désigné selon le flux d'entrée donné, qui disposera du nombre spécifique d'octets.  
  
> [!NOTE]  
>  Cette méthode a été déconseillée dans la spécification JDBC et son appel entraîne la levée d'une exception « Non implémenté ».  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setUnicodeStream(int n,  
                                   java.io.InputStream x,  
                                   int length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *n*  
  
 **Entier** qui indique le numéro du paramètre.  
  
 *x*  
  
 Objet InputStream.  
  
 *length*  
  
 Nombre d'octets.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setUnicodeStream est spécifiée par la méthode setUnicodeStream dans l’interface java. Sql. PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
