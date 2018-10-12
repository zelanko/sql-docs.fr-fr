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
manager: craigg
ms.openlocfilehash: 792b09cc57fbfb1438c6c4e9d372beb6547635d5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47697777"
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
  
 Un **chaîne** qui contient le nom du catalogue.  
  
 *schema*  
  
 **Chaîne** contenant le nom du schéma.  
  
 *table*  
  
 **Chaîne** qui contient le nom de la table.  
  
 *col*  
  
 Valeur **chaîne** qui contient le modèle du nom de la colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getColumnPrivileges est spécifiée par la méthode getColumnPrivileges dans l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getColumnPrivileges contiendra les informations suivantes :  
  
|Nom   |Type|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Nom du catalogue.|  
|TABLE_SCHEM|**String**|Le nom de schéma de table.|  
|TABLE_NAME|**String**|Le nom de la table.|  
|COLUMN_NAME|**String**|Nom de la colonne.|  
|GRANTOR|**String**|Objet octroyant l'accès.|  
|GRANTEE|**String**|Objet bénéficiant de l'accès.|  
|PRIVILEGE|**String**|Type d'accès octroyé.|  
|IS_GRANTABLE|**String**|Indique si le bénéficiaire peut accorder ou non l'accès à d'autres utilisateurs.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getColumnPrivileges, consultez « sp_column_privileges (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a> Exemple  
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
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
