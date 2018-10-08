---
title: Méthode getMaxCursorNameLength (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxCursorNameLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2cd2bed9-adf4-4bcd-ae5a-d0e3428bc709
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e81bef95caaade2ffbb7d112027ec0d0be9b77f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47604357"
---
# <a name="getmaxcursornamelength-method-sqlserverdatabasemetadata"></a>Méthode getMaxCursorNameLength (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre maximal de caractères autorisé par cette base de données dans un nom de curseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getMaxCursorNameLength()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique le nombre maximal de caractères autorisés.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getMaxCursorNameLength est spécifiée par la méthode getMaxCursorNameLength dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
