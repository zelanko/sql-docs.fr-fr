---
title: "Méthode executeUpdate (java.lang.String, java.lang.String) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerStatement.executeUpdate (java.lang.String[])
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 2f44a689-65c8-4c94-9574-e9c08ea7918e
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b81258e1175ae7aa752556145dbaa2573bb15d8d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="executeupdate-method-javalangstring-javalangstring"></a>Méthode executeUpdate (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Exécute l’instruction SQL fournie et les signaux [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] que les clés générées automatiquement indiquées dans le tableau spécifié doivent être disponibles pour la récupération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               java.lang.String[] columnNames)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *SQL*  
  
 A **chaîne** qui contient une instruction SQL.  
  
 *columnNames*  
  
 Un tableau de type **chaîne** qui indique les noms de colonne des clés générées automatiquement doivent être disponibles.  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique le nombre de lignes affectées, 0 si vous utilisez une instruction DDL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode executeUpdate est spécifiée par la méthode executeUpdate dans l’interface java.sql.Statement.  
  
 Si l’exécution d’une procédure stockée entraîne un nombre de mises à jour qui est supérieur à un, ou qui génère plusieurs jeux de résultats, utilisez le [exécuter](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) méthode à exécuter la procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode executeUpdate &#40; SQLServerStatement &#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
