---
title: getmoreresults, méthode (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMoreResults (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6419e5a8-8b3a-4d5b-8226-95865c52c723
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ad7363db0cb1de986273e59d698e2f1b00d50deb
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779100"
---
# <a name="getmoreresults-method-int"></a>Méthode getMoreResults (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Passe au résultat suivant de cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) et traite tous les objets actuellement ouverts du jeu de résultats suivant les instructions spécifiées par le mode donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final boolean getMoreResults(int mode)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *mode*  
  
 Un **int** qui indique comment gérer des objets du jeu de résultats actuellement ouverts. Il doit s’agir de l’une des constantes suivantes :  
  
 CLOSE_CURRENT_RESULT  
  
 KEEP_CURRENT_RESULT (non pris en charge par le pilote JDBC)  
  
 CLOSE_ALL_RESULTS  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si le résultat retourné est un jeu de résultats. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMoreResults est spécifiée par la méthode getMoreResults dans l’interface java.sql.Statement.  
  
 Si la méthode getMoreResults est appelée avant la récupération des résultats, elle se comporte comme spécifié par l’argument *mode* et passe au résultat suivant.  
  
> [!NOTE]  
>  Le pilote JDBC ne prend pas en charge la constante KEEP_CURRENT_RESULT. Si elle est utilisée, une exception est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [getMoreResults, méthode &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
