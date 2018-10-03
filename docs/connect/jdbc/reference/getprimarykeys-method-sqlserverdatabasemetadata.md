---
title: Méthode getPrimaryKeys (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getPrimaryKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ebfe236a-dc02-493e-a3ab-5353d3769e36
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73c1f5576d440cc9c98708882b98c5b6d9ceff42
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809977"
---
# <a name="getprimarykeys-method-sqlserverdatabasemetadata"></a>Méthode getPrimaryKeys (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des colonnes de clés primaires de la table donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getPrimaryKeys(java.lang.String cat,  
                                         java.lang.String schema,  
                                         java.lang.String table)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *cat*  
  
 Un **chaîne** qui contient le nom du catalogue.  
  
 *schema*  
  
 **Chaîne** contenant le nom du schéma.  
  
 *table*  
  
 **Chaîne** qui contient le nom de la table.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getPrimaryKeys est spécifiée par la méthode getPrimaryKeys dans l’interface java.sql.DatabaseMetaData.  
  
 Le jeu de résultats retourné par la méthode getPrimaryKeys contient les informations suivantes :  
  
|Nom   |Type|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|String|Nom de la base de données qui contient la table spécifiée.|  
|TABLE_SCHEM|String|Schéma de la table.|  
|TABLE_NAME|String|Nom de la table.|  
|COLUMN_NAME|String|Nom de la colonne.|  
|KEY_SEQ|short|Numéro séquentiel de la colonne dans une clé primaire multicolonne.|  
|PK_NAME|String|Nom de la clé primaire.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les données retournées par la méthode getPrimaryKeys, consultez « sp_pkeys (Transact-SQL) » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser la méthode getPrimaryKeys pour retourner des informations sur les clés primaires de la table Person.Contact dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetPrimaryKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getPrimaryKeys("AdventureWorks", "Person", "Contact");  
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
  
  
