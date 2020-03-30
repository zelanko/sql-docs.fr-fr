---
title: setBinaryStream, méthode (int, java.io.InputStream) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6c32b904-c44b-472e-a084-38f008a742b4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 483588eee0a5d1baaf7f2eda4a88372c45836d2e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67975308"
---
# <a name="setbinarystream-method-int-javaioinputstream"></a>Méthode setBinaryStream (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon le flux d'entrée spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setAsciiStream(int parameterIndex,  
                                 java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 **int** indiquant le numéro du paramètre.  
  
 *x*  
  
 Objet java.io.InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setBinaryStream est spécifiée par la méthode setBinaryStream de l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [setBinaryStream, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setbinarystream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
