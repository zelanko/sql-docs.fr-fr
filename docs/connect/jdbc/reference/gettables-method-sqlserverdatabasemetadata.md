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
ms.openlocfilehash: e8dfd7f14d6006f5a41a7cd2a9b0cae4933804fe
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979214"
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
  
 **Chaîne** contenant le nom du catalogue. La spécification d'une valeur Null pour ce paramètre indique que le nom du catalogue n'a pas besoin d'être utilisé.  
  
 *schema*  
  
 **Chaîne** contenant le modèle de nom du schéma. La spécification d'une valeur Null pour ce paramètre indique que le nom du schéma n'a pas besoin d'être utilisé.  
  
 *tableName*  
  
 **String** contenant le modèle de nom de la table.  
  
 *types*  
  
 Tableau de chaînes qui contient les types de tables à inclure. Null indique que tous les types de tables doivent être inclus.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTables est spécifiée par la méthode getTables de l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getTables contient les informations suivantes :  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**Chaîne**|Nom de la base de données qui contient la table spécifiée.|  
|TABLE_SCHEM|**Chaîne**|Le nom du schéma de la table.|  
|TABLE_NAME|**Chaîne**|Nom de la table.|  
|TABLE_TYPE|**Chaîne**|Le type de table.|  
|Remarques|**Chaîne**|Description de la table.<br /><br /> **Remarque :** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne retourne pas de valeur pour cette colonne.|  
|TYPE_CAT|**Chaîne**|Non pris en charge par le pilote JDBC.|  
|TYPE_SCHEM|**Chaîne**|Non pris en charge par le pilote JDBC.|  
|TYPE_NAME|**Chaîne**|Non pris en charge par le pilote JDBC.|  
|SELF_REFERENCING_COL_NAME|**Chaîne**|Non pris en charge par le pilote JDBC.|  
|REF_GENERATION|**Chaîne**|Non pris en charge par le pilote JDBC.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getTables, consultez « sp_tables (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Exemple  
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
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
