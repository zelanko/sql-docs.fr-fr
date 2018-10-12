---
title: Méthode getTables (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getTables
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a7514673-3457-4541-9560-28a8284ad9e3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: caabbe281791120a4f3b162029cb86dd340ffc28
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730467"
---
# <a name="gettables-method-sqlserverdatabasemetadata"></a>Méthode getTables (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des tables disponibles dans le modèle de nom de catalogue, de schéma ou de table donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getTables(java.lang.String catalog,  
                                    java.lang.String schema,  
                                    java.lang.String table,  
                                    java.lang.String[] types)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalog*  
  
 Un **chaîne** qui contient le nom du catalogue. La spécification d'une valeur Null pour ce paramètre indique que le nom du catalogue n'a pas besoin d'être utilisé.  
  
 *schema*  
  
 **Chaîne** contenant le modèle de nom du schéma. La spécification d'une valeur Null pour ce paramètre indique que le nom du schéma n'a pas besoin d'être utilisé.  
  
 *tableName*  
  
 **String** contenant le modèle de nom de la table.  
  
 *types*  
  
 Tableau de chaînes qui contient les types de tables à inclure. Null indique que tous les types de tables doivent être inclus.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getTables est spécifiée par la méthode getTables de l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getTables contient les informations suivantes :  
  
|Nom   |Type|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Nom de la base de données qui contient la table spécifiée.|  
|TABLE_SCHEM|**String**|Le nom de schéma de table.|  
|TABLE_NAME|**String**|Le nom de la table.|  
|TABLE_TYPE|**String**|Le type de table.|  
|REMARKS|**String**|Description de la table.<br /><br /> **Remarque :** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne retourne pas de valeur pour cette colonne.|  
|TYPE_CAT|**String**|Non pris en charge par le pilote JDBC.|  
|TYPE_SCHEM|**String**|Non pris en charge par le pilote JDBC.|  
|TYPE_NAME|**String**|Non pris en charge par le pilote JDBC.|  
|SELF_REFERENCING_COL_NAME|**String**|Non pris en charge par le pilote JDBC.|  
|REF_GENERATION|**String**|Non pris en charge par le pilote JDBC.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getTables, consultez « sp_tables (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser la méthode getTables pour retourner des informations de description de la table Person.Contact dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetTables(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTables("AdventureWorks", "Person", "Contact", null);  
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
  
  
