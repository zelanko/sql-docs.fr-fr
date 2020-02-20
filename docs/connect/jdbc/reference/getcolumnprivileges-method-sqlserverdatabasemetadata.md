---
title: Méthode getColumnPrivileges (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getColumnPrivileges
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ab6a671-9573-4b95-8c23-364306c60d25
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ae80a8c33f68ad2f3d2c85b1343a5cc0f2b423c5
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67952877"
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
  
 **Chaîne** contenant le nom du catalogue.  
  
 *schema*  
  
 **Chaîne** contenant le nom du schéma.  
  
 *table*  
  
 **Chaîne** qui contient le nom de la table.  
  
 *col*  
  
 Valeur **chaîne** qui contient le modèle du nom de la colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getColumnPrivileges est spécifiée par la méthode getColumnPrivileges de l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getColumnPrivileges contiendra les informations suivantes :  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**Chaîne**|Nom du catalogue.|  
|TABLE_SCHEM|**Chaîne**|Le nom du schéma de la table.|  
|TABLE_NAME|**Chaîne**|Nom de la table.|  
|COLUMN_NAME|**Chaîne**|Nom de la colonne.|  
|GRANTOR|**Chaîne**|Objet octroyant l'accès.|  
|GRANTEE|**Chaîne**|Objet bénéficiant de l'accès.|  
|PRIVILEGE|**Chaîne**|Type d'accès octroyé.|  
|IS_GRANTABLE|**Chaîne**|Indique si le bénéficiaire peut accorder ou non l'accès à d'autres utilisateurs.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getColumnPrivileges, consultez « sp_column_privileges (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode getColumnPrivileges pour retourner les droits d’accès de la colonne FirstName de la table Person.Contact dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
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
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
