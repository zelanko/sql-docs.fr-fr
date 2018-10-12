---
title: createStatement, méthode (int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.createStatement (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 90dbf639-c3d8-4519-9300-5447c79aec17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58390bfd2310b1cae9ce7427106c88a8e38915df
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645367"
---
# <a name="createstatement-method-int-int"></a>Méthode createStatement (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) qui génère des objets [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) avec la concurrence et le type donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Statement createStatement(int resultSetType,  
                                          int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *resultSetType*  
  
 Valeur **int** représentant le type du jeu de résultats.  
  
 *resultSetConcurrency*  
  
 Valeur **int** représentant le type de concurrence du jeu de résultats.  
  
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
  
  
