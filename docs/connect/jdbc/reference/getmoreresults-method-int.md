---
title: "Méthode getMoreResults (int) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.getMoreResults (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6419e5a8-8b3a-4d5b-8226-95865c52c723
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0daf7ce3684ce376ea228adcc9e4b2c0d32f831b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getmoreresults-method-int"></a>Méthode getMoreResults (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Passe au résultat suivant de ce [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet et traite les résultats actuellement ouverts set (objets) en fonction des instructions spécifiées par le mode donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final boolean getMoreResults(int mode)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *mode*  
  
 Un **int** qui indique comment gérer des objets du jeu de résultats actuellement ouverts. Doit être une des constantes suivantes :  
  
 CLOSE_CURRENT_RESULT  
  
 KEEP_CURRENT_RESULT (non pris en charge par le pilote JDBC)  
  
 CLOSE_ALL_RESULTS  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si le résultat retourné est un jeu de résultats. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMoreResults est spécifiée par la méthode getMoreResults dans l’interface java.sql.Statement.  
  
 Si la méthode getMoreResults est appelée avant l’extraction des résultats, il se comporte comme spécifié par le *mode* argument et passe au résultat suivant.  
  
> [!NOTE]  
>  Le pilote JDBC ne prend pas en charge la constante KEEP_CURRENT_RESULT. Si elle est utilisée, une exception est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getMoreResults &#40; SQLServerStatement &#41;](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
