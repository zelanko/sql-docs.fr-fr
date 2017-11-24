---
title: "Méthode getTableTypes (SQLServerDatabaseMetaData) | Documents Microsoft"
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
apiname: SQLServerDatabaseMetaData.getTableTypes
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: e0f5dc57-07b8-4811-ab1a-80a524bfdb42
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1d4bda5e46fac353d28458eabb2090eb3915e84c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="gettabletypes-method-sqlserverdatabasemetadata"></a>Méthode getTableTypes (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les types de tables disponibles dans la base de données actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getTableTypes()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTableTypes est spécifiée par la méthode getTableTypes dans l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getTableTypes contient les informations suivantes :  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|TABLE_TYPE|**Chaîne**|Le type de table.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getTableTypes, consultez « sp_tables (Transact-SQL) » dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] la documentation en ligne.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode getTableTypes pour retourner les informations de type de table dans le [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] exemple de base de données, étant donné que la base de données est spécifié dans la chaîne de connexion.  
  
```  
public static void executeGetTableTypes(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTableTypes();  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
