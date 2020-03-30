---
title: Méthode getIndexInfo (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getIndexInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a677cc6-8e33-4e57-8678-0849345aa8d0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8dd512236aa3070ce299756d4e4294c79ac2e94a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67982790"
---
# <a name="getindexinfo-method-sqlserverdatabasemetadata"></a>Méthode getIndexInfo (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des index et statistiques pour la table donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getIndexInfo(java.lang.String cat,  
                                       java.lang.String schema,  
                                       java.lang.String table,  
                                       boolean unique,  
                                       boolean approximate)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *cat*  
  
 **Chaîne** contenant le nom du catalogue.  
  
 *schema*  
  
 **Chaîne** contenant le nom du schéma.  
  
 *table*  
  
 **Chaîne** qui contient le nom de la table.  
  
 *unique*  
  
 **true** si seuls les index des valeurs uniques sont retournés. **false** si tous les index sont retournés.  
  
 *approximate*  
  
 **true** si les résultats reflètent des valeurs approximatives ou obsolètes. **false** si les résultats sont exacts.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getIndexInfo est spécifiée par la méthode getIndexInfo de l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getIndexInfo contient les informations suivantes :  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**Chaîne**|Nom de la base de données qui contient la table spécifiée.|  
|TABLE_SCHEM|**Chaîne**|Schéma de la table.|  
|TABLE_NAME|**Chaîne**|Nom de la table.|  
|NON_UNIQUE|**boolean**|Indique si les valeurs d'index peuvent ne pas être uniques.|  
|INDEX_QUALIFIER|**Chaîne**|Nom du propriétaire de l’index. Il peut avoir la valeur Null lorsque TYPE correspond à tableIndexStatistic.|  
|INDEX_NAME|**Chaîne**|Nom de l’index.|  
|TYPE|**short**|Type de l’index. Ce peut être l’une des valeurs suivantes :<br /><br /> tableIndexStatistic (0)<br /><br /> tableIndexClustered (1)<br /><br /> tableIndexHashed (2)<br /><br /> tableIndexOther (3)|  
|ORDINAL_POSITION|**short**|Position ordinale de la colonne dans l'index. La première colonne dans l'index est 1.|  
|COLUMN_NAME|**Chaîne**|Nom de la colonne.|  
|ASC_OR_DESC|**Chaîne**|Ordre utilisé dans le classement de l'index. Ce peut être l’une des valeurs suivantes :<br /><br /> A (croissant)<br /><br /> D (décroissant)<br /><br /> NULL (non applicable)<br /><br /> **Remarque :**  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] retourne toujours « A ».|  
|CARDINALITY|**int**|Nombre de lignes dans la table ou de valeurs uniques dans l'index.|  
|PAGES|**int**|Nombre de pages utilisées pour le stockage de l'index ou de la table.|  
|FILTER_CONDITION|**Chaîne**|Condition de filtrage.<br /><br /> **Remarque :**  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] retourne toujours Null.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getIndexInfo, consultez « sp_indexes (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser la méthode getIndexInfo pour retourner des informations sur les index et les statistiques de la table Person.Contact dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetIndexInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getIndexInfo("AdventureWorks", "Person", "Contact", false, true);  
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
  
  
