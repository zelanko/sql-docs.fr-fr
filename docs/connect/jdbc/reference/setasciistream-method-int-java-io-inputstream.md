---
title: setAsciiStream, méthode (int, java.io.InputStream) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02c2443d-44e1-4f16-a0d5-08d197838214
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5520e84dc049a3aa395e62b4df94331d50fd8d63
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711357"
---
# <a name="setasciistream-method-int-javaioinputstream"></a>Méthode setAsciiStream (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le numéro du paramètre désigné à l’objet java.io.InputStream donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setAsciiStream(int parameterIndex,  
                                 java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 Un **int** qui indique le numéro de paramètre.  
  
 *x*  
  
 Un objet java.io.InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode setAsciiStream est spécifiée par la méthode setAsciiStream dans l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a> Voir aussi  
 [setAsciiStream, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
