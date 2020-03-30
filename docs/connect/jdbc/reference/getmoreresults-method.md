---
title: Méthode getMoreResults () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMoreResults ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: df89db50-0b2f-4094-820a-30be25ad72fe
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dcbce9783641376ae142e94ab5e45dc47fe16fef
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67981730"
---
# <a name="getmoreresults-method-"></a>Méthode getMoreResults ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Passe au résultat suivant de cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final boolean getMoreResults()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le résultat retourné est un jeu de résultats. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMoreResults est spécifiée par la méthode getMoreResults de l’interface java.sql.Statement.  
  
 L’appel de la méthode getMoreResults ferme implicitement tous les objets actuellement ouverts du jeu de résultats qui ont été obtenus avec la méthode [getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [getMoreResults, méthode &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
