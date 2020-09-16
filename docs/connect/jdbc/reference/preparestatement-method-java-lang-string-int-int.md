---
description: Méthode prepareStatement (java.lang.String, int, int)
title: prepareStatement, méthode (java.lang.String, int, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5bb96dbe-f673-41b5-911b-8f661cca071a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9cbb24ea7e33779665b80a8a967f739df4b74baa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432911"
---
# <a name="preparestatement-method-javalangstring-int-int"></a>Méthode prepareStatement (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un objet [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) qui génère des objets [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) avec le type et la concurrence donnés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sSql,  
                                                   int resultSetType,  
                                                   int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sSql*  
  
 **String** contenant une instruction SQL.  
  
 *resultSetType*  
  
 **int** indiquant le type du jeu de résultats.  
  
 *resultSetConcurrency*  
  
 **int** indiquant le type de concurrence du jeu de résultats.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet PreparedStatement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode prepareStatement est spécifiée par la méthode prepareStatement de l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, méthodes](../../../connect/jdbc/reference/sqlserverconnection-methods.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
