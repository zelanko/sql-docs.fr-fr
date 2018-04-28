---
title: Méthode getColumnPrivileges (SQLServerDatabaseMetaData) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getColumnPrivileges
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ab6a671-9573-4b95-8c23-364306c60d25
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b88af8e4af62f556bd22a3769d587ad214a1273
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getcolumnprivileges-method-sqlserverdatabasemetadata"></a>Méthode getColumnPrivileges (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des droits d'accès aux colonnes d'une table.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getColumnPrivileges(java.lang.String catalog,  
                                              java.lang.String schema,  
                                              java.lang.String table,  
                                              java.lang.String col)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalog*  
  
 A **chaîne** qui contient le nom du catalogue.  
  
 *schema*  
  
 A **chaîne** qui contient le nom du schéma.  
  
 *table*  
  
 A **chaîne** qui contient le nom de table.  
  
 *col*  
  
 A **chaîne** qui contient le modèle de nom de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getColumnPrivileges est spécifiée par la méthode getColumnPrivileges dans l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getColumnPrivileges contient les informations suivantes :  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Nom du catalogue.|  
|TABLE_SCHEM|**String**|Nom du schéma de table.|  
|TABLE_NAME|**String**|Le nom de la table.|  
|COLUMN_NAME|**String**|Nom de la colonne.|  
|GRANTOR|**String**|Objet octroyant l'accès.|  
|GRANTEE|**String**|Objet bénéficiant de l'accès.|  
|PRIVILEGE|**String**|Type d'accès octroyé.|  
|IS_GRANTABLE|**String**|Indique si le bénéficiaire peut accorder ou non l'accès à d'autres utilisateurs.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getColumnPrivileges, consultez « sp_column_privileges (Transact-SQL) » dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] la documentation en ligne.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode getColumnPrivileges pour retourner les droits d’accès de la colonne FirstName de la table Person.Contact dans le [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] base de données exemple.  
  
```  
public static void executeGetColumnPrivileges(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getColumnPrivileges("AdventureWorks", "Person", "Contact", "FirstName");  
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
  
  
