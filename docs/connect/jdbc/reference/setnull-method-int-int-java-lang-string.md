---
title: Méthode setNull (int, int, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setNull (int, int, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 43c74e06-2858-49ba-bae7-b88808e5fff4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8e59b32581d25370fa86da417fd71c1eb7b67b33
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67973578"
---
# <a name="setnull-method-int-int-javalangstring"></a>Méthode setNull (int, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné avec une valeur Null, en fonction du type et du nom du paramètre à définir.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setNull(int paramIndex,  
                          int sqlType,  
                          java.lang.String typeName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *paramIndex*  
  
 **int** indiquant le numéro du paramètre.  
  
 *sqlType*  
  
 Code de type JDBC défini par java.sql.Types.  
  
 *typeName*  
  
 **Chaîne** indiquant le nom complet du paramètre en cours de définition.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setNull est spécifiée par la méthode setNull de l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [setNull, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
