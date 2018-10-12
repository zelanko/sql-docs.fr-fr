---
title: SetFloat, méthode (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setFloat
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 26d861da-bb6a-4197-8b32-13dc7781c2bb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: caee7a8263997955b1199b906c6ac216bed4cd66
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722947"
---
# <a name="setfloat-method-sqlservercallablestatement"></a>Méthode setFloat (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon la valeur **float** donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setFloat(java.lang.String sCol,  
                     float f)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *f*  
  
 Un **float** valeur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode setFloat est spécifiée par la méthode setFloat de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
