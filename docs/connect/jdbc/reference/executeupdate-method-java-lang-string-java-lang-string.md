---
description: executeUpdate, méthode (java.lang.String, java.lang.String)
title: executeUpdate, méthode (java.lang.String, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate (java.lang.String[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2f44a689-65c8-4c94-9574-e9c08ea7918e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 037521938c5a28c6d40159a19151f8b84438a8e8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437641"
---
# <a name="executeupdate-method-javalangstring-javalangstring"></a>executeUpdate, méthode (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Exécute l’instruction SQL donnée et signale à [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] que les clés générées automatiquement indiquées dans le tableau donné doivent être récupérables.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               java.lang.String[] columnNames)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sql*  
  
 **Chaîne** contenant une instruction SQL.  
  
 *columnNames*  
  
 Tableau de type **String** indiquant quels noms de colonnes des clés générées automatiquement doivent être disponibles.  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant le nombre de lignes affectées, ou 0 en cas d’instruction DDL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode executeUpdate est spécifiée par la méthode executeUpdate de l’interface java.sql.Statement.  
  
 Si l’exécution d’une procédure stockée aboutit à plusieurs mises à jour, ou si cela génère plusieurs jeux de résultats, utilisez la méthode [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) pour exécuter la procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [executeUpdate, méthode &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
