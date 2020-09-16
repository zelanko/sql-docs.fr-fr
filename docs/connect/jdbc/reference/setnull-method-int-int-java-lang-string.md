---
description: Méthode setNull (int, int, java.lang.String)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca79b47de812ff19fc41aba38994dd73c80cbd4f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458634"
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
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
