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
manager: jroth
ms.openlocfilehash: 99d01841ca24cc1a7e34864b42018dac51fa1861
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66768229"
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
  
## <a name="see-also"></a>Voir aussi  
 [createStatement, méthode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
