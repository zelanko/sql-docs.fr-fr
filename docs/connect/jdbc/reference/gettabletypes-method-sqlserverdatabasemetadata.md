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
manager: jroth
ms.openlocfilehash: 6795a84a042a7abaa52fe83f562911c934709f81
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779060"
---
# <a name="gettabletypes-method-sqlserverdatabasemetadata"></a>Méthode getTableTypes (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les types de tables disponibles dans la base de données actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getTableTypes()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTables est spécifiée par la méthode getTables de l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getTableTypes contient les informations suivantes :  
  
|Créer une vue d’abonnement|Type|Description|  
|----------|----------|-----------------|  
|TABLE_TYPE|**String**|TT = Type de table|  
  
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
  
  
