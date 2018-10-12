---
title: createStatement, méthode (int, int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.createStatement (int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2e4fa385-8f61-4394-8f75-3e839930a57d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d07029a2f076c4342c715ac6c9fac38325d1a9a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666057"
---
# <a name="createstatement-method-int-int-int"></a>Méthode createStatement (int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) qui génère des objets [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) avec le type, la concurrence et la capacité de mise en attente donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Statement createStatement(int nType,  
                                          int nConcur,  
                                          int nHold)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *resultSetType*  
  
 Valeur **int** représentant le type du jeu de résultats.  
  
 *nConcur*  
  
 Valeur **int** représentant le type de concurrence du jeu de résultats.  
  
 *nHold*  
  
 Valeur **int** représentant la capacité de mise en attente.  
  
## <a name="return-value"></a>Valeur retournée  
 L’objet d’instruction.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode createStatement est spécifiée par la méthode createStatement dans l’interface java.sql.Connection.  
  
## <a name="see-also"></a> Voir aussi  
 [createStatement, méthode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
