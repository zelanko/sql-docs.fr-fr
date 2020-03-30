---
title: Méthode getTableTypes (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getTableTypes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e0f5dc57-07b8-4811-ab1a-80a524bfdb42
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8da791a53d6ee25dd56f7f015ccc69947999f3b9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979156"
---
# <a name="gettabletypes-method-sqlserverdatabasemetadata"></a>Méthode getTableTypes (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les types de tables disponibles dans la base de données actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getTableTypes()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTableTypes est spécifiée par la méthode getTableTypes de l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getTableTypes contient les informations suivantes :  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TABLE_TYPE|**Chaîne**|Le type de table.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getTableTypes, consultez « sp_tables (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode getTableTypes pour retourner des informations sur les types d’une table dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)], si la base de données est spécifiée dans la chaîne de connexion.  
  
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
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
