---
title: getAsciiStream (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getAsciiStream(int paramIndex)
apilocation:
- SQLServerCallableStatement.getAsciiStream(int paramIndex)
apitype: Assembly
ms.assetid: 9d8b235e-4208-40ee-b5a5-bc76f73b82f8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4c6ed0abcdd8d18a40cbf7ee9448af55270a81be
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954243"
---
# <a name="getasciistream-int"></a>getAsciiStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné sous forme de flux de caractères **ASCII** en fonction de l’index de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.io.InputStream getAsciiStream(int paramIndex)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *paramIndex*  
  
 **Entier** qui indique l’index du paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>Voir aussi  
 [getAsciiStream, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getasciistream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
