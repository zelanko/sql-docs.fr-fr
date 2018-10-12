---
title: setNull, méthode (java.lang.String, int, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setNull (java.lang.String, int, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 16ff77f9-7928-415c-abf6-97ed59e3e396
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 75d36097c8fad4f15b06497561ff52dbfcea19ff
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827847"
---
# <a name="setnull-method-javalangstring-int-javalangstring"></a>Méthode setNull (java.lang.String, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné avec une valeur Null, en fonction du type et du nom du paramètre à définir.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setNull(java.lang.String sCol,  
                    int nType,  
                    java.lang.String sTypeName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 Un **chaîne** contthat contient aining le nom du paramètre.  
  
 *%nLes*  
  
 Code de type JDBC défini par java.sql.Types.  
  
 *sTypeName*  
  
 Un **chaîne** qui indique le nom qualifié complet du paramètre qui est défini.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode setNull est spécifiée par la méthode setNull de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a> Voir aussi  
 [setNull, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setnull-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
