---
title: prepareStatement, méthode (java.lang.String, int[]) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String, int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 72b5c4a5-1382-4b2c-80a0-47c97c5f52d3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1bec0d56782a7e9cacd236011c79aba2ab2c806a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814487"
---
# <a name="preparestatement-method-javalangstring-int"></a>Méthode prepareStatement (java.lang.String, int[])
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un objet [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) servant à envoyer des instructions SQL paramétrables à la base de données et capable de retourner les clés générées automatiquement désignées par le tableau donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sql,  
                                                   int[] columnIndexes)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sql*  
  
 Un **chaîne** qui contient une instruction SQL.  
  
 *columnIndexes*  
  
 Un tableau d'entiers.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet PreparedStatement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode prepareStatement est spécifiée par la méthode prepareStatement dans l’interface java.sql.Connection.  
  
## <a name="see-also"></a> Voir aussi  
 [prepareStatement, méthode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
